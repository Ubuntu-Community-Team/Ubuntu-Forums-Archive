---
title: "Empty file in in home directory?1"
date: 2007-06-20
forum: General Help
---

### Post by corenominal on 2007-06-20
I have an empty file named "1" in my home directory, it is owned by root. Does anyone know what this is for or why it is there? I like to keep a clean house when it comes to file storage and this single file is beginning to annoy me. I'd like to  delete it but before I do I would like to know it's safe to do so. Has anyone else come across this?

---

### Post by bapoumba on 2007-06-20
> **corenominal said:**
> I have an empty file named "1" in my home directory, it is owned by root. Does anyone know what this is for or why it is there? I like to keep a clean house when it comes to file storage and this single file is beginning to annoy me. I'd like to  delete it but before I do I would like to know it's safe to do so. Has anyone else come across this?
No idea.
If you right click on the file, what is it stated in "properties"? What kind of file is this?

---

### Post by az on 2007-06-20
Open a terminal and run

sudo nautilus

 Go to /home/(your username) and delete it.

---

### Post by Rui Pais on 2007-06-20
> **az said:**
> Open a terminal and run

sudo nautilus

 Go to /home/(your username) and delete it.

why not just 
sudo rm ~/1

(we may avoid read something like "oops i deleted home by mistake is that bad..." ;) )

---

### Post by AZzKikR on 2007-06-20
Oh please, do not suggest running Nautilus using sudo, because one delete action and you might regret your life for ever.

sudo nautilus is DANGEROUS. Prone to deleting unwanted stuff. Do not do that, unless you are so very, very sure what you are doing.

---

### Post by LaRoza on 2007-06-20
If you want to use a graphical app, like Nautilus, do not use sudo, use gksudo. 

Doing this is dangerous, as you can really mess up your system.

---

### Post by az on 2007-06-20
Using gksudo or running sudo from the command line is the same thing.

The file is owned by root, so it needs root priviledges to get removed.  Mucking about with the command line when you are not familiar with it is just as dangerous as using a GUI file manager to delete stuff.

Whatever.

If you are going to tell someone to use "~", you may as well tell them what it means and what keys to press to make that character appear.  And that also assumes that there is only one user on the system, the one with sudo privs.

---

### Post by CrispyFried on 2007-06-20
> **az said:**
> Using gksudo or running sudo from the command line is the same thing.


there are well documented problems when running sudo with gui programs.

use gksudo.

---

### Post by Rui Pais on 2007-06-20
> **az said:**
> Using gksudo or running sudo from the command line is the same thing.

Thats one of the most dearest myths of Ubuntu Linux, those who pronounce those words will be burn by the community :lol:

> The file is owned by root, so it needs root priviledges to get removed.  Mucking about with the command line when you are not familiar with it is just as dangerous as using a GUI file manager to delete stuff.

Whatever.


If you are going to tell someone to use "~", you may as well tell them what it means and what keys to press to make that character appear.  And that also assumes that there is only one user on the system, the one with sudo privs.

Now you lost me, what the number of users or they powers have to do with "~"? 

And why should i explain the meaning of "~"? Do you explained the meaning of sudo? or all commands you give around? common, thats a plain remove of an empty file on user directory :lol:

---

### Post by AZzKikR on 2007-06-20
> **az said:**
> The file is owned by root, so it needs root priviledges to get removed.  Mucking about with the command line when you are not familiar with it is just as dangerous as using a GUI file manager to delete stuff.

What do you think is easier?

[LIST=1]
[*]Open terminal
[*]Start typing: sudo rm -R ./directory/
[*]Apply password
[*]See your directory removed
[/LIST]

or

[LIST=1]
[*]Open terminal (or ALT+F2, for this example)
[*]Type (gk)sudo nautilus
[*]Apply password
[*]Hit the delete key on the directory
[/LIST]

I would apply for the second one. This has its dangers: it's very and much easier to unwantedly move directories and files to another directory by just dragging/dropping them, or deleting the wrong directory. It's not the first time I experienced that myself.

Sure, it has the same effect, but if you don't immediately close the ROOT nautilus window (thinking you may use it later, walk away from your computer, get back in an hour),  you may forget it, and do stupid actions you'll regret later.

---

### Post by dannyboy79 on 2007-06-20
> **AZzKikR said:**
> What do you think is easier?

[LIST=1]
[*]Open terminal
[*]Start typing: sudo rm -R ./directory/
[*]Apply password
[*]See your directory removed
[/LIST]

or

[LIST=1]
[*]Open terminal (or ALT+F2, for this example)
[*]Type (gk)sudo nautilus
[*]Apply password
[*]Hit the delete key on the directory
[/LIST]

I would apply for the second one. This has its dangers: it's very and much easier to unwantedly move directories and files to another directory by just dragging/dropping them, or deleting the wrong directory. It's not the first time I experienced that myself.

Sure, it has the same effect, but if you don't immediately close the ROOT nautilus window (thinking you may use it later, walk away from your computer, get back in an hour),  you may forget it, and do stupid actions you'll regret later.

i go for the 1st but not the way you wrote it. I would
alt-f2
sudo rm /path/filename OR sudo rm -rf /path (IF you want to remove a directory and everything in it)

---

### Post by az on 2007-06-20
> **CrispyFried said:**
> there are well documented problems when running sudo with gui programs.

use gksudo.

Exactly what documented problems?

They are both exactly the same.  You escalate your privs in exactly the same way.  One shows a dialogue box to enter your password, the other uses the command line.

> **Rui Pais said:**
> 
Now you lost me, what the number of users or they powers have to do with "~"? 

And why should i explain the meaning of "~"? Do you explained the meaning of sudo? or all commands you give around? common, thats a plain remove of an empty file on user directory :lol:

If the file is in the non-admin user's directory, to use sudo, you have to log into the admin user's account.  From there, ~ will point to the admin user's home directory and not the other user's.

> **AZzKikR said:**
> What do you think is easier?

[LIST=1]
[*]Open terminal
[*]Start typing: sudo rm -R ./directory/
[*]Apply password
[*]See your directory removed
[/LIST]

or

[LIST=1]
[*]Open terminal (or ALT+F2, for this example)
[*]Type (gk)sudo nautilus
[*]Apply password
[*]Hit the delete key on the directory
[/LIST]

I would apply for the second one. This has its dangers: it's very and much easier to unwantedly move directories and files to another directory by just dragging/dropping them, or deleting the wrong directory. It's not the first time I experienced that myself.


I would think the second one is easier.  As well, if you screw up, you have a better chance at figuring out what you did wrong, since just about anybody who has used a computer knows how to drag and drop.   People are not idiots.  However, giving them a command line to run does not help them out if they mess it up.  For example, how many people realize that the command-line in Linux is case-sensitive?

Using the GUI is easier, so people will make fewer mistakes.

---

### Post by Rui Pais on 2007-06-20
> **az said:**
> If the file is in the non-admin user's directory, to use sudo, you have to log into the admin user's account.  From there, ~ will point to the admin user's home directory and not the other user's.
.
From 1st post:
> **corenominal said:**
> I have an empty file named "1" in my home directory, it is owned by root.

Whats the ambiguity? 





Is this something personal?

---

### Post by dannyboy79 on 2007-06-20
> **az said:**
>  Exactly what documented problems? 

Based on the last few posts you've made, might I suggest you should research a topic slightly before making statements that aren't tru, there is a difference when using sudo or gksudo. You can read all about it here and you'll have your answer: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
(NOTE: if the author got a nickel everytime someone linked to his page, he'd be a millionaire)

> **az said:**
>  They are both exactly the same.  You escalate your privs in exactly the same way.  One shows a dialogue box to enter your password, the other uses the command line. 
This is just untrue, please read above link.



> **az said:**
>  If the file is in the non-admin user's directory, to use sudo, you have to log into the admin user's account.  From there, ~ will point to the admin user's home directory and not the other user's. 
~ points to the home directory of whoever is logged in, simply put. I don't really understand what the point of this is though.



> **az said:**
>  I would think the second one is easier.  As well, if you screw up, you have a better chance at figuring out what you did wrong, since just about anybody who has used a computer knows how to drag and drop.   People are not idiots.  However, giving them a command line to run does not help them out if they mess it up.  For example, how many people realize that the command-line in Linux is case-sensitive?
More than just the command-line is case-sensitive, just wanted to make sure you were aware of that.

> **az said:**
>  Using the GUI is easier, so people will make fewer mistakes. 
and also have the possibility of accidentally dragging the entire /etc directory into another directory, then when they restart, non of their settings for every single program are gone! You can't do that from the command line.
We'll just have to agree to disagree.

---

### Post by az on 2007-06-20
> **Rui Pais said:**
> 
Whats the ambiguity? ?

I just like to make things clear.  If the original poster is not the first-user on the system and cannot sudo, then 
sudo rm ~/1
will point to the wrong home directory.

> **Rui Pais said:**
> 

Is this something personal?

Not at all.  I have been insulted by many many great people many many times in the past!  I'm okay with it.
  Not that I have been insulted, we just seem to be dissagreeing.  

If you dissagree with someone on a forum, *you're supposed to say so* otherwise, what's the point of a forum?

---

### Post by CrispyFried on 2007-06-20
> **az said:**
> 
[sudo vs gksudo]

Exactly what documented problems?
They are both exactly the same.  You escalate your privs in exactly the same way.  One shows a dialogue box to enter your password, the other uses the command line.


sudo uses the user configuration files, whereas gksudo uses the roots configuration files.

read [here]("http://www.psychocats.net/ubuntu/graphicalsudo"), and follow the links that list the examples..

as for how common the sudo-with-gui-programs problems are, beats me as Ive run sudo with gui stuff and experienced no problems but why take the chance? now I use gksudo for gui stuff. figure its a good habit.

EDIT: I see dannyboy beat me to it as far as listing psychocats page, which is where I got the sudo-vs-gksudo info from in the 1st place.

---

### Post by bapoumba on 2007-06-20
corenominal, are you still in here ?

---

### Post by ashz on 2007-06-20
Lol exactly what i was thinking, i think they all went slightly off topic!!

---

### Post by drew boardman on 2007-06-20
I thought I my learn something following this post now I'm more confused than ever! I think corenominals gone home!

Drew

---

### Post by az on 2007-06-20
> **dannyboy79 said:**
> Based on the last few posts you've made, might I suggest you should research a topic slightly before making statements that aren't tru, there is a difference when using sudo or gksudo. 


> **CrispyFried said:**
> sudo uses the user configuration files, whereas gksudo uses the roots configuration files.


I was wrong.  Now, that was a helpful way to bring it up, thank you.

However, the gksudo manpage implies the opposite:
       Notice  that  all the magic is done by the underlying library, libgksu.
       Also notice that the library will decide if it should use su or sudo as
       backend  using the /apps/gksu/sudo-mode gconf key, if you call the gksu
       command. You can force the backend by using the gksudo command,  or  by
       using the --sudo-mode and --su-mode options.

The gksu gconf key is set to sudo.  There is no gksudo gconf key.


> **dannyboy79 said:**
> 
More than just the command-line is case-sensitive, just wanted to make sure you were aware of that.

WTF?

> **dannyboy79 said:**
> 
and also have the possibility of accidentally dragging the entire /etc directory into another directory, then when they restart, non of their settings for every single program are gone! You can't do that from the command line.
We'll just have to agree to disagree.

Yes, we disagree.  I think the command line is more dangerous to the user who is unfamiliar with it than the GUI.  You can just as easily wipe out your system using the command line.

> **CrispyFried said:**
> sudo uses the user configuration files, whereas gksudo uses the roots configuration files.


Please say that  (because that makes sense) instead of just saying it's dangerous.

> **bapoumba said:**
> corenominal, are you still in here ?

In the end, we are all just wanting to help.  Isn't it great how people in the Ubuntu community will fight over each other to help someone?

---

### Post by zero244 on 2007-06-20
I agree doing the sudo nautilus command is best for us noobs. I even have a shortcut to open nautilus with root privileges.
Ive never misused it (yet). I dont leave it open after Ive finished.
I do think the more you know about the command line the better, so if a situation comes up that requires the command line you can handle it.
The command line has saved me many times.

---

### Post by az on 2007-06-21
> **zero244 said:**
> I agree doing the sudo nautilus command is best for us noobs. .

You mean, **gksudo nautilus**, right?  Sudo uses the user configuration files, whereas gksudo uses the root's configuration files and that can cause problems when you run the application as a normal user again.

---

