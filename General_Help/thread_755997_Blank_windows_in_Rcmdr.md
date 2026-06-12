---
title: "Blank windows in Rcmdr"
date: 2008-04-15
forum: General Help
---

### Post by fyazici on 2008-04-15
I have the latest R (R-2.6.2) and R commander (1.3-14). When I go to Tools menu (for example) pull down "load packages" in Rcmdr, a blank window is up and there is nothing in it.  This also happens with the other functions like in Graphs menu. I know that Rcmdr uses Tcl/Tk interface. I do not have this experience with other programs like amsn. Before asking any help from R-site, I like to learn from you that if this is related to Ubuntu configuration or not. I found a similar post in this forum, but there is no answer for it.

My Ubuntu 7.10 is up to date

Thanks for your help

[COLOR="Silver"]library(Rcmdr)
Loading required package: tcltk
Loading Tcl/Tk interface ... done
Loading required package: car

Rcmdr Version 1.3-14

> Error in get(paste("on", toupper(letter), sep = "")) : 
  variable "on&#304;" was not found[/COLOR]

---

