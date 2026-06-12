---
title: "For Dummies -&gt; howto start a command with BYOBU"
date: 2014-04-05
forum: General Help
---

### Post by nicolasdiogo on 2014-04-05
hello,


i am setting up a system that requires a command to be started with the desktop.
that is easily done.

but how can i start that command inside BYOBU?

would like to then login with ssh and fire up byobu and see the state of this command.

i have tried to solve this requirement by researching - but the discussions found on forums are not conculsive.


thanks for your suggestions,

---

### Post by Mark Phelps on 2014-04-05
There are additional links on the web page that may be of help: [https://help.ubuntu.com/community/Byobu]("https://help.ubuntu.com/community/Byobu")

---

### Post by nicolasdiogo on 2014-04-05
thanks Mark,

but it is the same again.

a lot of info on how to customise Byobu

but not in the sense of usage..

i suppose i am looking for a switch similar to what *screen* has ( -X ):
[http://stackoverflow.com/questions/6064548/send-commands-to-a-gnu-screen](http://stackoverflow.com/questions/6064548/send-commands-to-a-gnu-screen)


tchau

---

### Post by Lars Noodén on 2014-04-05
[byobu](http://manpages.ubuntu.com/manpages/trusty/en/man1/byobu.1.html) seems to be just a wrapper for screen (or tmux).  If you have not specified tmux, then it defaults to screen.  Either way, options are passed on to screen (or tmux) so try just treating it like you would screen and see if that works.

---

### Post by nicolasdiogo on 2014-04-11
hi,

i can not understand how to have BYOBU connecting to the screen session yet.

but i have just used SCREEN instead.

```

screen -d -m -S mycommandHere

```

thanks for your clarification,

---

### Post by nicolasdiogo on 2014-07-13
closing as solved

thanks,

---

