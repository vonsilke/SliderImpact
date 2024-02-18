# SliderImpact (WIP)

[Shape Keys Shader](#shape-keys-shader)

[Menu Shader](#menu-shader)

## Shape Keys Shader

```ini
;Example
[ResourcePosition]
[ResourcePosition.Base]
filename = 
[ResourcePosition.1]
filename = 
[Constants]
global persist $Key = 0
post ResourcePosition = copy_desc ResourcePosition.Base
post run = CommandListComputeShapeKeys

[CommandListComputeShapeKeys]
Resource\Shape\Key = copy ResourcePosition.Base
cs-t50 = copy ResourcePosition.Base
cs-t51 = copy ResourcePosition.1
x88 = $Key
;number of verts in pos.
$\Shape\KeyBatch = 0
run = CustomShader\Shape\Keys
```

## Menu Shader
```ini
;Example
[CommandListCursors.2]
;NORMALIZE VAR
local $v = (($Key2+1)/2)
;DRAW CURSOR
x5 = $bar_y*res_height/res_width
y5 = $bar_y
z5 = $v*$bar_x+$bar_xo-($bar_y*res_height/res_width)/2
w5 = $bar2_yo
ps-t100 = ResourceCursor2
run = CustomShader\Menu\Element
;DRAW ICON
x5 = $icon_size
y5 = $icon_size*res_width/res_height
z5 = $bar_xo-$icon_size
w5 = $bar2_yo
ps-t100 = ResourceSliderIcon2
run = CustomShader\Menu\Element
```