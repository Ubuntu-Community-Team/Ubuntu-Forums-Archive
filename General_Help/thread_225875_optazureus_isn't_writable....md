---
title: "opt/azureus isn't writable..."
date: 2006-07-30
forum: General Help
---

### Post by Nathan Otis on 2006-07-30
I am attempting to update Azureus with GTK graphical libraries that it says it needs. I am getting an error message that /opt/azureus isn't writable and that this update will probably fail. The error advises me to check permissions and try again. I've found the folder in question but can't change any permissions to make it writable.

I have also searched the forums but haven't found this specific issue and wasn't sure I should try anything that wasn't specifically answering this issue.

Azureus runs fine without this update, but the message at the beginning is a bit bothersome.

n.

---

### Post by topgi on 2006-07-30
You have to install Azureus in your home directory. Just make a folder caller Azureus and intall there. It is pretty straightforward.

---

### Post by Nathan Otis on 2006-07-30
Ah, I see. I'll give it a shot. Thank you.

Is it advisable to always install to my home directory?

n.

---

### Post by xen on 2006-07-30
I also had a similar problem, even with it installed in my home directory. Ubuntu has this library installed as a shared component, which differs to the one Azureus wants to install.

I think it was fixed by installing the file manually.

---

### Post by topgi on 2006-07-30
Azureus is a Java application. You have just to un-tar the files in a directory in your home. That's it.


____________________________________________________________________________

Other usefull info in : [http://ubuntufriends.wordpress.com/]("http://ubuntufriends.wordpress.com/")

---

### Post by taurus on 2006-07-30
> **Nathan Otis said:**
> Ah, I see. I'll give it a shot. Thank you.

Is it advisable to always install to my home directory?

n.
If you are the only user on your machine or only one to use that program, then install it in your home directory under ~/bin.  I've never had any problem with it, updating and what not...

---

### Post by mic959 on 2006-08-03
taurus and others

just my two cents

$ sudo chown -R [username] /opt/azureus

Worked perfectly for me.  I am assuming you got azureus from automatix.  I tried the repo one but I hated the sys tray bug.  Anyways its not like i'm on a corp net, so as long as you are the su, I don't see why not doing this.  Does anyone think this is a bad idea, security?

---

### Post by bionnaki on 2006-08-04
yeah, chown [username] will work.

also, if you open a terminal and type "sudo /opt/azureus/azureus" and then run the updates once or twice, the program will updated.

---

