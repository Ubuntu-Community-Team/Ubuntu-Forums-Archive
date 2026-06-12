---
title: "putty screen problem"
date: 2007-12-28
forum: General Help
---

### Post by spx3 on 2007-12-28
I'm connecting through putty to a linux server and want to run screen on it,
however there are some shortcuts in /etc/screerc and when I use CTRL in
putty I simply can't execute those,what can I do ?
CTRL+left should go to the screen on the left
same with CTRL+right,
and those don't work,but the putty screen just flashes like a bell alarm or
something.
how could this be fixed ?

```

addacl spx2
startup_message off
hardstatus alwayslastline "%{=b}%{G} %{b}%w %=%{r} F9=New F10=Detach F12=Quit %{kG}%C%A"
bindkey '^[[1;5D' prev
bindkey '^[[1;5C' next
bindkey -k k9 screen
bindkey -k F2 quit
bindkey -k k; detach
select 0


```

this is the important part of my /etc/screenrc

I've also tried this
[http://anti.teamidiot.de/nei/2007/02/irssi_putty_screen_unicode_utf/](http://anti.teamidiot.de/nei/2007/02/irssi_putty_screen_unicode_utf/)

For information about the bindings in screenrc I found this useful
[http://www.pixelbeat.org/lkdb/screen.html](http://www.pixelbeat.org/lkdb/screen.html)
and this
[http://www.rackaid.com/resources/linux-tutorials/general-tutorials/linux-screen.cfm](http://www.rackaid.com/resources/linux-tutorials/general-tutorials/linux-screen.cfm)

---

