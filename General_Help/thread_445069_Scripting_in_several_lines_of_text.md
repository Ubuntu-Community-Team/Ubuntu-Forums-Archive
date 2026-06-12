---
title: "Scripting in several lines of text"
date: 2007-05-15
forum: General Help
---

### Post by UncleB on 2007-05-15
Hi all,

I'm looking to script the whole setup of VNC to resumable sessions. (I keep building and killing PCs while I learn the OS!)

So I'm having trouble with changing the gdm.conf file. I want to replace the place holder ```
 [xdmcp]
``` with 

```
[xdmcp]
Enable=true
HonorIndirect=false
```

It's straightforward enough to replace one single line with a sed command but to replace one line with three confounds me.

How would I go about doing this?

Alternatively, is gdm.conf totally standard? Could I just get a 'good' copy and paste it in?

And for a third option or can I call a text file to pipe in to an area of text?

Any suggestions welcomed.

---

### Post by lloyd_b on 2007-05-16
It's just a matter of putting some "\n"s into the sed command.  Here's a sample:
```
lloyd@laptop:~/stuff$ echo "[xdmcp]" | sed 's/\[xdmcp\]/\[xdmcp\]\nEnable=true\nHonorIndirect=false/'
[xdmcp]
Enable=true
HonorIndirect=false
```

Note the escapes on the "[" and "]" characters - without the "\" to escape them, they are interpreted to produce substantially different results...

Lloyd B.

---

### Post by UncleB on 2007-05-16
Hi Lloyd,

I just spent a couple of hours re-writing your solution a million different ways with no success... on my Mac.

I then tried it on a Linux box and it worked exactly as you said.


Doh! Doh! And thrice doh!!!


Well, I've learned two lessons with this one at least.


Thank you very much!

---

