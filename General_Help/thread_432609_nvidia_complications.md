---
title: "nvidia complications"
date: 2007-05-04
forum: General Help
---

### Post by toastyjojio on 2007-05-04
hiya. runnin a toshiba sat.pro with geforce4 420 go/ just picked up new version of fiesty ubuntu.
being linux-new, i tried playing with the new "desktop effects" button: i was offered a driver for my card so as to take advantage of my "3D capabilities", etc. fine, says itinstalled, etc.

upon restart: zip, nada, nothing but a scary poltergeist-looking screen going black and white, black and white....

for now i just reinstalled fiesty and won't touch that button...

however, y'all seem to be doin' things in a terminal or something....i am only just figuring my way thru synaptic, so this part of the learning curve seems steep..........????shall i assume that this is a result of running your 'puters off a "recovery" mode from bootup? (question 1)

if so, i hope i will soon understand what folks are talking about....i would like to play silly desktop-effect-games, just like the other reindeer. as well, i am sure there are likely new frontiers in graphics-watching that i am unable to participate in.

so my command line starts off in /root...?????where/how do i go from there to find my nvid card drivers so i can type in the wondrous codes and ciphers i see on many a forum?
(question 2)

thanky kindly, even a penny will do

joji!

---

### Post by DJMatty on 2007-05-04
Hi

I had all sorts of problems with my 8800 nvidia card, until i installed the 9755 drivers manually... i also had problems using the standard desktop effects that came with ubuntu feisty, I ended up installing beryl and playing with that.

As to your questions, when you start your terminal, if you logged into ubuntu as root then you will get a terminal that runs as root. However the standard install should ask you for a user and you log in as that, and the terminal will run as that user, which is MUCH safer as it won't let you do things in the terminal that could cause major problems. If you need to run a particular command as root then you can use the 'sudo' command in front of the command and it will then ask for your users password, and temporarily run that command as root. e.g. sudo nano /etc/modprobe.d/init will run nano as root and will let you edit the init file.

Also this article is the one i used to install the latest nvidia drivers manually on my pc for my 8800 card:

[http://albertomilone.com/latest_nvidia_udsf_edgy.html](http://albertomilone.com/latest_nvidia_udsf_edgy.html)

The thing is that every time you update the o/s and it rebuilds the kernel you will need to reinstall the nvidia drivers every time by hand... but it works for me :)

Matt

---

