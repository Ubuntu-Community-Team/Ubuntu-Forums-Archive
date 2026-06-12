---
title: "How to start programs autmatically"
date: 2005-10-22
forum: General Help
---

### Post by tomach on 2005-10-22
My question is: 
how can i start some programs or command at startup process where should i put htem?? i mean when system reboot i want to start some programs automatically .... i know that i can put it in some scripts in rc.0 in etc but where exactly??

Thanks,
TOm

---

### Post by KingBahamut on 2005-10-22
System > Preferences > Session 

Youll find a tab at the top for startup. 

Input the commands you want to go in there to occur at startup.

---

### Post by tomach on 2005-10-22
yeee thanks but i was thinking more about editing some text files, im more interested in doing it by myslef, i like when i know where everhign is ;) so any ideas?
 i guess everhign is in etc

---

### Post by rimmer on 2005-10-22
If you want to run a script at start-up, the first thing you need to do is write a start-up script, put the script in the /etc/init.d folder. Then you need to update the system, run this from the shell "sudo update-rc.d myscriptname defaults", and that should add the program to the start-up sequence.
You can use a existing init script for a template, as for writing the script (if you don't know how to) I would suggest reading this, [linuxcommand]("http://www.linuxcommand.org/")
or/and this, however this in not ubuntu specific but it should give you a idea 
[enterprise.linux]("http://enterprise.linux.com/article.pl?sid=05/08/02/1821218&tid=129")
about what's  happening.

---

### Post by tomach on 2005-10-22
thanks thats the answer for my question!!!

---

### Post by tomach on 2005-10-27
Ok i tried it, but i would like to start programs that are under gnome...so where should i put it/??? I mean I want it only for one pofile hmmmm so any ideas??? I put it allready in init.d but there its for all and even not working cos i guess gnome starts too late....and do u know where gnome starts exaclty....maybe some startx is ;)))??

---

### Post by Peter76 on 2005-10-27
you have to make/edit an .Xsession file in your home directory. There should be an example xsession file somewhere on your system, which explains this in more detail... 
# locate xsession

Or, as i'm thinking now, try to find out which files the gui app changes. ( should be the same? )

---

