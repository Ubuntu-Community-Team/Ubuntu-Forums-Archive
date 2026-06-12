---
title: "computer no longer will display photos #2"
date: 2023-09-02
forum: General Help
---

### Post by jgw on 2023-09-02
I rebuilt my system with a new motherboard.  Now I cannot see .jpg files anymore.  Ubuntu thinks that they are text folders.  Gimp and Shotwell will not show them either.  Again, I have no idea why this is.  I have just spent over an hour trying to find a solution and I failed.  

Thoughts?

---

### Post by guiverc on 2023-09-03
> **jgw said:**
> Ubuntu thinks that they are text folders.  Gimp and Shotwell will not show them either.  ..  Thoughts?

I'd firstly ask the OS what they are, is this what you've already done, eg.

```

guiverc@d7050-next:~$   file d7*.jpg
d755_5_1864787.jpg:         JPEG image data, JFIF standard 1.01, resolution (DPI), density 96x96, segment length 16, baseline, precision 8, 1680x1050, components 3
d755_5_1864787_kdepart.jpg: JPEG image data, JFIF standard 1.01, resolution (DPI), density 96x96, segment length 16, baseline, precision 8, 1680x1050, components 3
guiverc@d7050-next:~$   file temp
temp: directory

```

ie. your response to `file` (or whatever you used) was a directory?

If that's your issue, I'd check drive health, or look for file-system damage.


Note:  not all JPG files will give the output I provided; I originally did a `file *.jpg` and got lots of variation of JPG  file metadata in the long list of output, thus redid it using the subset I've used for paste.

---

### Post by jgw on 2023-09-03
thank you for the reply.........

That computer will no longer start.  I was putting stuff on it and turned it off to check if was working.  Turned it back on and - nothing.  The power supply didn't even turn on.  It may be toast.

To answer your question.  The operating system thought that jpg files are all empty text folders.  Anyway, until I get that machine working again that's about all I can say.  

Thanks again!

---

### Post by yancek on 2023-09-03
If you right click on an image file icon, what shows?  It should show something like open with Image Viewer.  Does it show sometihng else?  There should be an option to Open with another application.

---

### Post by ajgreeny on 2023-09-03
I assume this is really a continuation of a previous thread of yours at [https://ubuntuforums.org/showthread.php?t=2490079](https://ubuntuforums.org/showthread.php?t=2490079)

My suggestion now that you can't even boot the computer is to remove the hard disk with your photos on and attach it to another computer to rescue all, or as many of them as you can.

With the info you have given us it is impossible to know where to go other than rescuing the situation as best you can, and the jpg problem may be a result of some other larger OS problem.

---

### Post by jgw on 2023-09-24
This is 3 weeks and this has now happened to me on another machine.  Here is what I have so far:
This computer has a new ubuntu 22.04.3 (+ new update).  It thinks that a .jpg file is a text file and its empty.

[code]
file India-050.jpg
India-050.jpg: empty

Same file - other computer:
file India-050.jpg
India-050.jpg: JPEG image data, JFIF standard 1.01, resolution 340x1560, components 3(DPI), density 72x72, segment length 16, baseline, precision 8, 2
[code]

Find system info here: https://termbin.com/bw4n

I have tried to have a different programs (like gimp and shotwell which think they are text files too) to get it to show me the image of the .jpg file and got nothing.   

This happened to me on another computer and I remember that it just stopped doing this and started to recognize jpg files.  I have no idea of what I did or what the machine did.  

I did a google search and this seems to be a regular problem.  I also did a search here but couldn't find anything that helped.  

Anybody have any ideas on this one?

I am going to put this in another message - this one is too old. I will also set this a solved.............

---

