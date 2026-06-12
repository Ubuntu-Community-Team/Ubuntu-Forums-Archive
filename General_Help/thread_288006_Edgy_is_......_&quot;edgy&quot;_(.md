---
title: "Edgy is ...... &quot;edgy&quot; :("
date: 2006-10-29
forum: General Help
---

### Post by Tommerz on 2006-10-29
hey guys,

Just installed the new Edgy straight from cd (fresh installation) and found a couple of problems, which were not present in Dapper.

1. I can no longer hold "ctrl + alt +f1" to go to an independent terminal, instead I get a collection of funky odd colours, and have to switch back into tty7.

2. Detection of my video settings using the fabled old "dpkg-reconfigure xserver-xorg" doesn't seem to detect my settings anywhere near as well as dapper or breezy did - it gives the wrong manufacturer and refresh rates :( 

Does anyone have any ideas why these features are lacking? It seems as though Edgy may have been rushed out too early and a few kinks haven't been worked out. Any news of patches?

---

### Post by taurus on 2006-10-29
1.  I can't check with that right now since my newly Edgy is in the office.  Don't feel like riding my bike in today but may do that later this afternoon if there is nothing much happening around here.

2.  If you need to edit your /etc/X11/xorg.conf to include the refreshing rates, you can do that with (in recovery mode if you wish...)

```
nano -Bw /etc/X11/xorg.conf
```
Again, Dapper is a LTS (long term support, 3 years) while Edgy is a bleeding edge.  Sometimes bleeding edge doesn't work out of a box for everybody.  Don't forget Dapper was delated for a few weeks for more testing...

---

### Post by Tommerz on 2006-10-29
Sorry if my previous post came across as tho I was rubbishing Ubuntu or Edgy, I think it's great piece of software and it's amazing what people are able to offer for free!!

> 1. I can't check with that right now since my newly Edgy is in the office. Don't feel like riding my bike in today but may do that later this afternoon if there is nothing much happening around here.
One of the advantages of using Ubuntu is it gives you something to do if things get quiet :) 

> 2. If you need to edit your /etc/X11/xorg.conf to include the refreshing rates, you can do that with (in recovery mode if you wish...)

Unfortunately, I'm not entirely sure what the monitors refresh rates are!! What I might do, is run the same program on a dapper live cd, then copy the updated xorg.conf file across onto the Edgy installation :p 

> Again, Dapper is a LTS (long term support, 3 years) while Edgy is a bleeding edge. Sometimes bleeding edge doesn't work out of a box for everybody. Don't forget Dapper was delated for a few weeks for more testing...

Hmm, I didn't realise that the Edgy final release was still meant to be that bleeding edge, I assumed it would be similar to breezy + hoary in terms of.... err.... "edgyness"

Maybe in a few months some of the edges will be "smoothed out" via patches. :)

---

