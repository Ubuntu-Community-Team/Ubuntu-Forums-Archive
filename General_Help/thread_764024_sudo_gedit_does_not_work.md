---
title: "sudo gedit does not work"
date: 2008-04-23
forum: General Help
---

### Post by benfrasersimpson on 2008-04-23
I tried to use the command sudo gedit to edit a file, but the text editor program opens about 5 minutes later, and crashes without opening the file.
I have also tried using gksudo, but no difference. Sudo works for every other program i tested. I have also reinstalled gedit, but this doesnt help.
Thanks in advance for your help.

---

### Post by kellemes on 2008-04-23
> **benfrasersimpson said:**
> I tried to use the command sudo gedit to edit a file, but the text editor program opens about 5 minutes later, and crashes without opening the file.
I have also tried using gksudo, but no difference. Sudo works for every other program i tested. I have also reinstalled gedit, but this doesnt help.
Thanks in advance for your help.

You better use gksudo indeed..
Is there any output when gedit crashes?

---

### Post by benfrasersimpson on 2008-04-23
Nope, there is no output.
and gksudo does not work for me either.
Thanks for your quick reply.

---

### Post by MagnuzNilzzon on 2008-04-29
Does anyone have any more information on this problem? I've also encountered it, in the same way. 

//magnus

---

### Post by benfrasersimpson on 2008-04-29
Magnus, what version of ubuntu are you using?
And have you changed anything on it?
The only things i have really changed is im using Ndiswrapper for my wireless card and i have installed virtualbox, although the problem started before that.
Hopefully we can sort this out!
Im using 8.04.

---

### Post by Nunu on 2008-04-29
And sudo -s gedit?

---

### Post by MagnuzNilzzon on 2008-04-30
I'm running 8.04 too, and the only program affected was Gedit, graying out and ceasing to respond when called with sudo gedit. It worked when not in sudo. 

I tried sudo -s gedit, and it gave this: 

magnus@xanthos:~$ sudo -s gedit
/usr/bin/gedit: /usr/bin/gedit: cannot execute binary file

But after I tried that, ordinary sudo gedit worked again. Very odd.

---

### Post by Nunu on 2008-04-30
Did you guys upgrade to 8.04? I have seen a few people having simular issues and it seems to be an upgrade problem. Looks like clean installs aren't affected buy this bug

When you use sudo -s gedit give the filename to for instance

> sudo -s gedit examplefile

---

### Post by benfrasersimpson on 2008-04-30
ben@ben-desktop:~$ sudo -s gedit /usr/bin/iriverter
/usr/bin/gedit: /usr/bin/gedit: cannot execute binary file

I get that error with sudo -s
My sudo gesit works after doing this as well though, although it takes a while to work.

Mine is a clean install of ubuntu 8.04
Any ideas?
Thanks!

---

### Post by MagnuzNilzzon on 2008-05-01
Clean install of 8.04 for me too

---

### Post by seanbickford on 2008-08-25
Total newb here, 1st time post.

Same exact symptoms as given here. sudo works for everything else except gedit. using gksudo will pop up a gedit window 5-6 minutes later which contains no text and immediately crashes. sudo -s reveals same error "cannot execute binary file". Also using 8.04, clean install. Pretty frustrating. Any other options?

---

### Post by Skorzen on 2008-08-25
And without sudo, it still crashes?
Have you tried with other text editors, like nano?

---

### Post by -Zeus- on 2008-08-25
> **kellemes said:**
> You better use gksudo indeed..
Is there any output when gedit crashes?

I have a clean install and it works fine.  kellemes, there is no need for gksu; sudo works just fine.

---

### Post by danbuter on 2008-08-25
Has anyone submitted a bug report?

---

### Post by Too Late on 2008-08-25
> **-Zeus- said:**
> kellemes, there is no need for gksu; sudo works just fine.
But it's not the same thing: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

