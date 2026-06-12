---
title: "Firefox 3 g_object_unref &amp; gdk_draw_image"
date: 2008-05-29
forum: General Help
---

### Post by huczek on 2008-05-29
Ubuntu 8.04 Hardy Heron x86
Firefox 3 beta 5 and Firefox 3 RC
output in terminal: errors while firefox running
```
(firefox:6773): Gdk-CRITICAL **: gdk_draw_image: assertion `GDK_IS_GC (gc)' failed

(firefox:6773): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```
The firefox often interrupts and exits. Even though I fixed [SCIM]("http://ubuntuforums.org/showthread.php?t=757070").
```
Segmentation fault
```

---

### Post by Klinsi on 2008-06-13
I have the same problem. Most of webpages works, but f.eg google give me this: 


[Firefox Google Bug - Screenshot]("http://img78.imageshack.us/img78/2893/firbugdn7.png")

```
(firefox:9102): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```

And this:

```
(firefox:9102): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial 12'

(firefox:9102): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial 12'

(firefox:9102): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Arial 12', text='English Hello'

(firefox:9102): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial Bold 9.75'

(firefox:9102): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial Bold 9.75'

(firefox:9102): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Arial Bold 9.75', text='English Hello'

(firefox:9102): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial 9.75'

(firefox:9102): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial 9.75'

(firefox:9102): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Arial 9.75', text='English Hello'

(firefox:9102): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial 7.5'

(firefox:9102): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial 7.5'

(firefox:9102): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Arial 7.5', text='English Hello'

(firefox:9102): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial 10.07421875'

(firefox:9102): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial 10.07421875'

(firefox:9102): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Arial 10.07421875', text='English Hello'

(firefox:9102): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial Bold 9.75'

(firefox:9102): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial 9'

(firefox:9102): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial 9'

(firefox:9102): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Arial 9', text='English Hello'

(firefox:9102): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial 7.5'

(firefox:9102): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial Bold 15'

(firefox:9102): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial Bold 15'

(firefox:9102): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Arial Bold 15', text='English Hello'
```

---

### Post by Klinsi on 2008-06-13
Ok, I maybe found a solution. 

I had a problem with Arial Font. To solve this problem I changed permissions for all Arial fonts, allowing others to read and exec these files. 
And it works.

---

