---
title: "Change Theme's Panel Seperator"
date: 2008-06-04
forum: General Help
---

### Post by twodayslate on 2008-06-04
I would like to change my themes panel separator. How would I go about doing that. I have already changed the handles. 

Here is an old unanswered thread asking the same thing. [http://ubuntuforums.org/showthread.php?p=5109710#post5109710](http://ubuntuforums.org/showthread.php?p=5109710#post5109710)

Thank you very much!

---

### Post by twodayslate on 2008-06-04
Found it. ```
  			image
    				{
       					function		= VLINE
       					recolorable		= TRUE
       					file				= "Lines/line-v.png"
       					border			= { 0, 0, 1, 1 }
       					stretch			= TRUE
    				}
```
edit://

I am trying to make the handle and the separator look that same but I am having trouble
```
	GtkPaned       ::handle-size          = 2
    			image
    				{
       					function		= VLINE
       					recolorable		= TRUE
       					file			= "Lines/line-v.png"
       					border			= { 0, 0, 1, 1 }
       					stretch			= TRUE
    				}
    			image
    				{
      					function		= HANDLE
       					recolorable		= TRUE
       					file			= "Lines/line-v.png"
       					border			= { 1, 0, 1, 1 }
       					overlay_stretch		= FALSE
      					orientation		= VERTICAL
    				}

``` [http://img111.imageshack.us/img111/3017/screenshotcm8.png](http://img111.imageshack.us/img111/3017/screenshotcm8.png)
Off by one px

---

### Post by twodayslate on 2008-06-05
Anyone good a themes? Is there a nother place to look?

edit:// I figured it out. Make the handle image 94x10

---

