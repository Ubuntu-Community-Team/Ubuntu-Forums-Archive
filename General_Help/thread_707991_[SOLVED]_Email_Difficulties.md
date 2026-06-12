---
title: "[SOLVED] Email Difficulties"
date: 2008-02-25
forum: General Help
---

### Post by ClearyA on 2008-02-25
Hey folks, So I'm new to Linux.  I followed the guide on how to send and receive your hotmail through evolution, but i would get an error message that said "unable to connect to POP server 127.0.0.1. Error sending username: -ERR Command not implemented" so i attempted to edit the /etc/hosts.allow file to add the line "hotwayd 127.0.01." with just a basic text editor, however when i attempt to save the file it says "permission denied, you cannot save this file" (something like that). I am the comps admin so should i not be able to edit this file?  Any ideas would be awesome! :)

---

### Post by suibhne on 2008-02-25
open the command line and type 
sudo su

-enter your password at the prompt-type 

nautilus

-now you should be able to navigate to your file graphically and edit your file, but i don't know if t'll solve your problem

---

### Post by Sam Lars on 2008-02-25
What guide is this?  Can you get mail from other servers?

---

### Post by DieB on 2008-02-25
You might have noticed, that although you are the administrator Ubuntu asks you sometimes for your password. This is due to the fact that on normal unix there is always a user "root" that has all the power and for normal u only login as root for doing administrational stuff. Ubuntu uses sudo that stands for super user do. this command assignes root power to the command following. like u might see beow in the example

on ubuntu the admin has to "allow" every administrational task. that means in your case u have to open the termial and type:

> sudo gedit [dir_to_file]

(gedit is the gnome editor if u like u can also use nano, vi, or kedit(only KDE))
after that it should be no problem to save that file after editing.

remember you need root rights whenever changing something on the system.

---

### Post by ClearyA on 2008-02-25
Thanks a lot, that did indeed allow me to edit the document, but it did not fix my evolution problem.  I still get the error message "unable to get to pop serve 217.0.0.1" and if i try to work around this by just pressing "send/receive mail" it says i must pay for webDAV access".  Is my attempt at making my hotmail account work through evolution hopeless? Any ideas, or perhaps another program which would work better? (Thanks a lot for all the previous help)

---

### Post by DieB on 2008-02-25
Please check once again if u set up all correct, cause the ip seems like your router or an internal server because of the .0.0.1 string. normally it works fine pop.[Webaddresse] or pop3[webaddresse] if it is a pop-server u try to get your mails from.

---

### Post by ClearyA on 2008-02-25
Thanks DieB, I figured it out. The problem was on the hotmail side of things. To prevent spam etc you must have a paid account to be able to hook evolution up with it. Thats what I have gathered from random posts etc. at least. Thanks for the help though!

---

### Post by Sam Lars on 2008-02-26
Yeah, you have to pay for Hotmail POP access.... when I realized that, that's when I stopped using Hotmail and switched to Lavabit and Bluebottle and Gmail...
You can mark this thread as solved so people can see that.

---

