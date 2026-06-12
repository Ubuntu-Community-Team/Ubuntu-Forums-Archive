---
title: "How install libfribidi-bin in Ubuntu 12.04?"
date: 2014-05-19
forum: General Help
---

### Post by Randymanme on 2014-05-19
I want to use UCK, the Ubuntu Customization Kit while using Ubuntu 12.04.  But the tutorial, [Roll Your Own Customized Ubuntu With UCK ]("http://www.linux.com/learn/tutorials/739139-roll-your-own-customized-ubuntu-with-uck"), at [http://www.linux.com/learn/tutorials/739139-roll-your-own-customized-ubuntu-with-uck](http://www.linux.com/learn/tutorials/739139-roll-your-own-customized-ubuntu-with-uck) says,

*A very important prequisite is to install **libfribidi-bin**. It is a required dependency that is not present in the **uck** package. If you don't install it your custom build will fail, when it is almost finished, with a "Failed to build gfxboot theme" error. This is is a bug going back to 12.04 or earlier, so sigh and deal with it.*
 
After much googling, I don't see how to install that package in Precise Pangolin.  Sysnaptic, however, does install UCK.  Does it work anyway, without libfribidi-bin?

 As usual, any help will be appreciated.  Thank you.):P

P.S.: My hardware won't support Unity beyond 12.04.

---

### Post by Randymanme on 2014-05-20
I tried it anyway and ,no, it doesn't work -- apparentlywithout libfribidi-bin.

---

### Post by Randymanme on 2014-05-29
[B][SOLVED] How do I install libfribidi-bin in Ubuntu 12.04?  
[/B]
Answered by [knudfl]("http://www.linuxquestions.org/questions/user/knudfl-386037/"), [COLOR=#000000][FONT=Verdana]LQ 5k Club:
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
# 5 .
Quote:
[TABLE="width: 100%"]
[TR]
[TD="class: bbcodeblock, bgcolor: #CFD9FF"]I still don't have libfribidi-bin.[/TD]
[/TR]
[/TABLE]

Yes you have : libfribidi-bin is one file = /usr/bin/fribidi

Which you already have from the installed libfribidi0 
[http://packages.ubuntu.com/precise/i...bidi0/filelist]("http://packages.ubuntu.com/precise/i386/libfribidi0/filelist")

Please read posts #2 and #4.


[/FONT][/COLOR]
[http://www.linuxquestions.org/questions/ubuntu-63/how-do-i-install-libfribidi-bin-in-ubuntu-12-04-a-4175505517/](http://www.linuxquestions.org/questions/ubuntu-63/how-do-i-install-libfribidi-bin-in-ubuntu-12-04-a-4175505517/)

---

