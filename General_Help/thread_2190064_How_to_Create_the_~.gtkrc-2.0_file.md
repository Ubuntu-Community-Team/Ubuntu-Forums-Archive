---
title: "How to Create the ~/.gtkrc-2.0 file?"
date: 2013-11-25
forum: General Help
---

### Post by tomsubt on 2013-11-25
Hi  Anyone?

---

### Post by oldos2er on 2013-11-25
Isn't this file created automatically on default Ubuntu? ```
touch .gtkrc-2.0
``` Or use your favorite text editor. ```
gedit .gtkrc-2.0
```

---

### Post by tomsubt on 2013-11-25
Ann  I dont know I am new at ubuntu but Thanks to the tip you gave  >>> gedit .gtkrc-2.0 <<<  I was able to create the file and edit the scroll bar size

but I made the scroll bar size too wide now and I would like to get back into this file and adjust the size but I dont know how to locate the file I get an error message on the terminal now which looks like the file does not exit when I paste in  "edit .gtkrc-2.0"  and the editor will not show. Do you know what I could be doing wrong?  Thanks  

PS:  I used this tip from this website to change the width of the scrollbar and it worked but need to make it smaller>>

    [http://ubuntuforums.org/showthread.php?t=1652483](http://ubuntuforums.org/showthread.php?t=1652483)

    Edit or create ~/.gtkrc-2.0 with these lines.
    Code:

    style "scroll"
    {
        GtkScrollbar::slider-width = 25
    }

    class "*" style "scroll"

    Adjust that number to your liking.

---

### Post by drmrgd on 2013-11-25
If I understand you, you typed (or copy / pasted) 
```

edit .gtkrc-2.0

```

You probably wanted to run 'gedit' though.  Try it with the 'g' in front of the command like this:

```

gedit ~/.gtkrc-2.0

```

---

### Post by tomsubt on 2013-11-25
> **drmrgd said:**
> If I understand you, you typed (or copy / pasted) 
```

edit .gtkrc-2.0

```

You probably wanted to run 'gedit' though.  Try it with the 'g' in front of the command like this:

```

gedit ~/.gtkrc-2.0

```

drmrgd:  Thank You Very Much, that  (g) in front did it. I was able to resize the scrollbar again.

Was wondering if you knew how to change the color of the scrollbar?

---

### Post by vasa1 on 2013-11-25
> **tomsubt said:**
> drmrgd:  Thank You Very Much, that  (g) in front did it. I was able to resize the scrollbar again.

Was wondering if you knew **how to change the color of the scrollbar**?

While you may get an answer here about changing the color of the scrollbar, I request you to start a separate thread with just that question so that people will know what is going on in that thread and read it if they're interested.

This way, judging from the title, no one will know that there's a question about scrollbars in here.

---

### Post by tomsubt on 2013-11-26
Ok, I will start a new post now, Thanks

---

