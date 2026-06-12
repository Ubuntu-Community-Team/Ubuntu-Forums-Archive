---
title: "SSH connection to continue running program after ssh session closed..."
date: 2007-12-24
forum: General Help
---

### Post by phillips321 on 2007-12-24
Hi guys,

Lets just say the time is 4:55pm and i finish at 5:00pm. I want to download a file that's ready for me by the time i get home so i ssh into my home pc from my work laptop.

I then run the command.

wget [http://domain.tld/file.etx](http://domain.tld/file.etx)

if this file is huge i wont be able to download it in time.

how can i exit the ssh session, shutdown my laptop at work and allow the wget to continue downloading?

Cheers for your help guys

---

### Post by bodhi.zazen on 2007-12-24
Use screen

[http://www.rackaid.com/resources/linux-tutorials/general-tutorials/linux-screen.cfm](http://www.rackaid.com/resources/linux-tutorials/general-tutorials/linux-screen.cfm)

---

### Post by p_quarles on 2007-12-24
You can also do this without installing anything extra: just add "nohup" to the beginning of the command. 
```
nohup  wget http://domain.tld/file.etx
```
Works like a charm.

---

### Post by mellowd on 2007-12-24
I agree with bodhi.zazen. Use screen, nice and simple.

[http://mellowd.co.uk/test2/index.php?entry=entry071201-063218](http://mellowd.co.uk/test2/index.php?entry=entry071201-063218)

---

### Post by phillips321 on 2007-12-24
cheers guys, screen works fine for my purpose.

just for those wondering the basics of screen are as follows:
[LIST]
[*]ssh into remote server
[*]run "screen"
[*]run any commands u want
[*]detach current screen session (Ctrl-A, d)
[*]exit ssh session
[/LIST]

to get back to the detached screen session:
[LIST]
[*]ssh into remote server
[*]run "screen -x"
[*]run any commands u want
[*]end screen session "exit"
[*]exit ssh session "exit"
[/LIST]

cheers for your help guys.

p.s. i'll also investigate the nohup command

---

