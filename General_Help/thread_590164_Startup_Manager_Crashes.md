---
title: "Startup Manager Crashes"
date: 2007-10-24
forum: General Help
---

### Post by rudeboyskunk on 2007-10-24
Every time I try to start my startupmanger, it crashes.  Here is what I get from command line:

> rudeboyskunk@timebomb-ubuntu:~$ sudo startupmanager
[sudo] password for rudeboyskunk:
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... found: (hd0,1)/home/rudeboyskunk/Templates/mars.xpm.gz

Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Traceback (most recent call last):
  File "/usr/bin/startupmanager", line 31, in <module>
    main()
  File "/usr/bin/startupmanager", line 28, in main
    app = startupmanager.main()
  File "/usr/lib/python2.5/site-packages/startupmanager/__init__.py", line 4, in main
    SumGui()
  File "/usr/lib/python2.5/site-packages/startupmanager/gtk_frontend.py", line 835, in __init__
    self.update_widgets()
  File "/usr/lib/python2.5/site-packages/startupmanager/gtk_frontend.py", line 672, in update_widgets
    0, False))
  File "/usr/lib/python2.5/site-packages/startupmanager/gtk_frontend.py", line 115, in convert_color
    return color_dict[color]
KeyError: 'blue/re'
rudeboyskunk@timebomb-ubuntu:~$ 


I'm sure it's obvious to somebody who understands what all that means.  Any ideas?

---

### Post by illuminaris on 2007-10-24
I noticed something weird, but it is probably my lack of knowledge that betrays me. Why are we running 14-generic instead of 16-generic, speaking of the kernal. Shouldn't we be in the most recent, and the highest number available?

I'm not recommending you change that, because I really have no idea what I'm talking about. It's just a question not a suggestion.

---

### Post by rudeboyskunk on 2007-10-25
*bump*

---

### Post by rudeboyskunk on 2007-10-26
*bump*

---

### Post by rudeboyskunk on 2007-10-28
*bump*

---

### Post by Flyn on 2007-10-29
I had this same problem, I got a hacky fix for you:
1. Open the file /usr/lib/python2.5/site-packages/startupmanager/gtk_frontend.py :

2. Go to line 92, you should see something like the following, but maybe with different colors being referenced:
```

    if wanted_type == 1:
        color_dict = {
        "black" : 0 ,
        "blue" : 1 ,
        "green" : 2 ,
        "cyan" : 3 ,
        "red" : 4 ,
        "magenta" : 5 ,
        "brown" : 6 ,
        "light-gray" : 7 ,
        "dark-gray" : 8 ,
        "light-blue" : 9 ,
        "light-green" : 10 ,
        "light-cyan" : 11 ,
        "light-red" : 12 ,
        "light-magenta" : 13 ,
        "yellow" : 14 ,
        "white" : 15
        }
```3. Now look for the line that says:

```
 "blue/red" : X ,
```Where X is a certain number.

4. Add a new line before or after that line:

```
 "blue/re" : X ,
```Making sure that X is the same number as in the original line.

You should be OK now.

Hope this helps. Also, yay me for making _UGLY_ hacks in a language I don't know! ;-)

---

### Post by rudeboyskunk on 2007-10-29
Ok, I tried, but I couldn't find a line that said "blue/red".  Is it possible to just insert it and the "blue/re" argument, or will that break the file?

---

### Post by Flyn on 2007-10-29
Hmm. Foiled.
Can you attach the file here so I can take a look?

---

### Post by rudeboyskunk on 2007-10-29
Sorry, it's too big, but here is what it says in that area:

> class Config:
    """Contain the data we need to the widgets."""
    glade_dir = 'startupmanager.glade'
    version = '1.0'

def convert_resolution(number):
    resolution = number[0]
    if resolution == "0":
        xres = "640"
        yres = "480"
    elif resolution == "1":
        xres = "800"
        yres = "600"
    elif resolution == "2":
        xres = "1024"
        yres = "768"
    elif resolution == "3":
        xres = "1280"
        yres = "1024"
    else:
        xres = "1600"
        yres = "1200"
    return xres, yres

def convert_color(color, wanted_type, revert):
    """Convert color name to combo box index."""
    if wanted_type == 0:
        color_dict = {
        "black" : 0 ,
        "blue" : 1 ,
        "green" : 2 ,
        "cyan" : 3 ,
        "red" : 4 ,
        "magenta" : 5 ,
        "brown" : 6 ,
        "light-gray" : 7
        }
    if wanted_type == 1:
        color_dict = {
        "black" : 0 ,
        "blue" : 1 ,
        "green" : 2 ,
        "cyan" : 3 ,
        "red" : 4 ,
        "magenta" : 5 ,
        "brown" : 6 ,
        "light-gray" : 7 ,
        "dark-gray" : 8 ,
        "light-blue" : 9 ,
        "light-green" : 10 ,
        "light-cyan" : 11 ,
        "light-red" : 12 ,
        "light-magenta" : 13 ,
        "yellow" : 14 ,
        "white" : 15
        }
    if revert:
        reverse_color_dict = dict((v,k) for (k,v) in color_dict.iteritems())
        return reverse_color_dict[color]
    else:
        return color_dict[color]

def convert_vga(vga, wanted, revert=False):
    """Convert vga number to combo box index."""
    dic = {
    769 : "00" ,
    771 : "10" ,
    773 : "20" ,
    775 : "30" ,
    796 : "40" ,
    758 : "01" ,
    788 : "11" ,
    791 : "21" ,
    794 : "31" ,
    798 : "41" ,
    786 : "02" ,
    789 : "12" ,
    792 : "22" ,
    795 : "32" ,
    799 : "42"
    }
    if revert:
        reverse_dic = dict((v,k) for (k,v) in dic.iteritems())
        return reverse_dic[vga]
    if dic.has_key(vga):
        settings = dic[vga]
    else:
        settings = dic[769]
    return int(settings[wanted])


---

### Post by Flyn on 2007-10-29
Can try either :

"blue/re" : 1 ,


Or

"blue/re" : 4 ,

---

### Post by rudeboyskunk on 2007-10-29
I tried it but it didn't work, but I'll reboot and see if that works.  I'll let you know.

---

### Post by rudeboyskunk on 2007-11-01
Ok, still doesn't work.  BAH.  There's already a bug report filed for it.

---

### Post by rudeboyskunk on 2007-11-06
*bump*

---

