---
title: "Can MyPaint install on your Lubuntu/Ubuntu system?"
date: 2015-01-11
forum: General Help
---

### Post by gilga2 on 2015-01-11
Hi
I'm trying to install mypaint (from sources and from repositories).
The installation works okay but I've got a strange error at launch after that:

```
Traceback (most recent call last):
  File "/home/susskind/Documents/mypaint-git/mypaint/gui/tileddrawwidget.py", line 789, draw_cb(self=<CanvasRenderer object at 0x7fe6cf3b0af0 (gui+tileddrawwidget+CanvasRenderer at 0x17be2e0)>, widget=<CanvasRenderer object at 0x7fe6cf3b0af0 (gui+tileddrawwidget+CanvasRenderer at 0x17be2e0)>, cr=<cairo.Context object>)
            # Render the document
            render_info = self.render_prepare(cr, None)
            self.render_execute(cr, *render_info)
  variables: {'cr': ('local', <cairo.Context object at 0x7fe6cf89f5f0>), 'None': ('builtin', None), 'self.render_prepare': ('local', <bound method CanvasRenderer.render_prepare of <CanvasRenderer object at 0x7fe6cf3b0af0 (gui+tileddrawwidget+CanvasRenderer at 0x17be2e0)>>), 'render_info': (None, [])}
  File "/home/susskind/Documents/mypaint-git/mypaint/gui/tileddrawwidget.py", line 905, render_prepare(self=<CanvasRenderer object at 0x7fe6cf3b0af0 (gui+tileddrawwidget+CanvasRenderer at 0x17be2e0)>, cr=<cairo.Context object>, device_bbox=(0, 0, 1338, 676))
            # calculate the final model bbox with all the clipping above
            x1, y1, x2, y2 = cr.clip_extents()
            if not self.is_translation_only():
  variables: {'y1': (None, []), 'x2': (None, []), 'x1': (None, []), 'y2': (None, [])}
AttributeError: 'cairo.Context' object has no attribute 'clip_extents'
``` 

Can someone tell whether MyPaint can install on his version of Lubuntu (or even Ubuntu)? I don't know whether it's a problem of dependencies or else? 
I'm on Lubuntu 14.10
Thanks

---

