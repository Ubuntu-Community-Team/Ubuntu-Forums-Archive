---
title: "CLIbuntu: New Ubuntu based Distro"
date: 2007-05-14
forum: General Help
---

### Post by moriancumer_12 on 2007-05-14
I'm not sure if this is the place to post this but, here it goes.
I'm in the process of developing a new Ubuntu-server based distro. 
Description:
Name:CLIbuntu
A commandline only distro with built-in tutorials for those hesitant to use the commandline. It will allow them to follow the tutorials, which are customized for the distro, and practice and apply the concepts side by side on the same system. Tutorials will include Linux/bash commands, configurations and console applications. I'll enable framebuffer so that you can view video and pictures. I'll develop a rsync script to easily download updated and new tutorials. I've just submitted this project to so sourceforge. 
I guess I like the idea of having the tutorials rolled up in it's own OS is for three main reasons:

1) The tutorials will be specific to the OS. If the tutorial was separate from the OS, there might be slight differences between distros which may cause some confusion/frustration when trying to follow the tutorial. This guarantees that's the tutorials work exactly as described.

2) If someone walks through a tutorial on setting up procmail, fetchmail and mutt for their pop email account. When they are done with the tutorial they instantly have a properly set up configuration ready to go on the same system. Also, my tutorial on installing software won't apply to rpm and slackware based distros.

3) Consiistency: Everyone will be drawing from the same respositories (unless they mess with sources.list), using the same version of software, same kernel and same system configuration and filesystem layout.

I chose text files is so the enduser can easily make their own notes or other changes within the tutorial itself as to their needs. For example, they might want to add their home network set up with their gateway and various machines names and IP addresses, so they can easily reference it later if they need to set up their network up again. 


Questions:
How do I get this project approved to be added to the 3rd party projects in the Ubuntu forum?
What is the process and legality of redesigning the Ubuntu logo for this new distro?


P.S. What are your thoughts about this new distro I'm developing?

Thanks,

---

### Post by Ateo on 2007-05-14
Feisty server edition is without GUI. What would be the difference? The tutorials? If just that, why not just develop a package that is that said tutorial and try to get it included in future releases?

It's a good idea. I like the idea of server with no GUI.

---

### Post by moriancumer_12 on 2007-05-15
I envision this project as the "Linux DESKTOP Distro with NO-GUI', so the system should be pre-configured as much as possible. This distro should be inviting for those new to the CLI. This is another reason I feel I should bundle the OS with tutorials. My tutorials focus more on doing what a user would normally do on an average GUI-desktop system. I want to demonstatrate that you can do 98% of everything you can do in the GUI can also be done in the CLI. 

Some of the pre-configuration I will be doing to make the CLI more friendly is activate framebuffer so the enduser can use fbi to view images and mplayer to play videos. Two applications in my 'office suite' will include a todo list scheduler which is a python script and calendar/appointment application which is a script as well. I will be writing a simple bash script which will easily launch these applications in the CLI and the tutorials for those applications will only deal with their functionality and usage. I also want to make it fun, by including flashy colorful prompts to liven things up. 

I want this environment to be as friendly as possible. I want the user to imediately be able to jump into the applications (which are pre-installed and configured) and start being productive as soon as possible without having to play around with configurations. This is intended for those shy or hesitant to the commandline. A straight Ubuntu-server install will not have this type of environment. 

I hope this makes sense. I know I'm targeting a narrow percentage of users out there, but I hope this clearifies why I want to make this project it's own distro. 

I feel like I'm not just providing tutorials but an experiece where the user can:
view and manipulate images
Watch videos, dvds
Listen to audio files, cds
Manipulate audio files
rip a cd
Type up a paper
Create a spreadsheet
create and view presentations
organized projects
browse the Internet
Instant message on Yahoo, MSN, AIM, Jabber, etc
ftp
Create web pages, blogs, etc
Use peer to peer 
use a window manager to use multiple apps at once
burn a cd or dvd
create your own DVD
play games
use email
keep an address book
and some much more....

Did you know you could do all that on the commandline? I don't think most new users ever realize how much you CAN do on the CLI. I'm hoping to provide a friendly environment where they can feel as comfortable as possible on the CLI.

Please let me know if I'm crazy or if you see flaws in this project? 

Thanks

---

### Post by hartz on 2007-05-16
Good idea, but I think your audience will be limited.

I wouldn't mind giving it a try, I use a GUI mostly because it is easy for web browsing and gives me resizeable terminal windows.

My suggestion:  Include mc as a default package.  Some people love it, others hate it.  (A bit like emacs I guess.)

And screen.  Screen is good.

---

### Post by moriancumer_12 on 2007-05-18
> **hartz3 said:**
> Good idea, but I think your audience will be limited.

I wouldn't mind giving it a try, I use a GUI mostly because it is easy for web browsing and gives me resizeable terminal windows.

My suggestion:  Include mc as a default package.  Some people love it, others hate it.  (A bit like emacs I guess.)

And screen.  Screen is good.

screen and mc will definitely be there.
Thanks

---

### Post by fragos on 2007-05-18
Not long ago Shutttleworth published the Ubuntu standing on trademarks.  CLIbuntu infringes on the trademark.  To use that name you will need permision.  There is however no problem basing a new distribution on Ubuntu as long as Ubuntu is given credit.  This is also covered in the trademark statement.

---

### Post by xavier_r on 2007-07-16
Lets add this package as a default interface for CLIbuntu
[https://sourceforge.net/projects/screenface](https://sourceforge.net/projects/screenface)

---

### Post by moriancumer_12 on 2007-07-19
> **xavier_r said:**
> Lets add this package as a default interface for CLIbuntu
[https://sourceforge.net/projects/screenface](https://sourceforge.net/projects/screenface)


Thanks, I really like this. I'll be contacting the dev. I've been working on a similar interface, but mine is more menu driven. He has added some great default apps. I'll see if we can collaborate. Thanks again.

---

### Post by xavier_r on 2007-07-20
> **moriancumer_12 said:**
> Thanks, I really like this. I'll be contacting the dev. I've been working on a similar interface, but mine is more menu driven. He has added some great default apps. I'll see if we can collaborate. Thanks again.

Hi, thanks for you appreciation... I would really love to collaborate...
Also, the packages at sourceforge are not up-to-date
The latest packages are available here
[http://screenface.66ghz.com](http://screenface.66ghz.com)

---

