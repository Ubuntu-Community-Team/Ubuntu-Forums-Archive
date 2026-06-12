---
title: "best understandable guide for newbies to configure 3d desktop?"
date: 2006-11-04
forum: General Help
---

### Post by noktekniq on 2006-11-04
so i spend countless hours reinstalling and formating ubuntu after so many failures of installing these 3d graphic desktop display. where can i get the best understandable guide which people can understand. 

i'm currently using nvidia 7800 with amd setup

---

### Post by po0f on 2006-11-04
noktekniq,

I would suggest getting used to Ubuntu and Linux in general before installing stuff like Beryl.  I have had no problems following the guides.  I think you are just not familiar enough with the commands.  Just play with Linux a couple of weeks, then come back to Beryl.

---

### Post by noktekniq on 2006-11-04
i have nothing to play around with. i don't have any programs besides the ones that were in the installation pack of ubuntu. i really like the cube desktop and all the eyecandy. that's why i wanted to switch over to ubuntu

---

### Post by s_h_a_d_o_w_s on 2006-11-04
I am the complete opposite of a newbie, have formatted countless times, installed everything a gazillion times. Beryl is not for newbies. Heck it's not even for me (even though i really want it :-( ). Become more accustomed to linux, sure. But most guides i've followed gave me the same error, or did nothing at all. And i followed the to the line. Beryl ids a pain to install, it should be there by default, but it's not. 

If you really need to get beryl running, and have the patience (i guess it's what i lack, all the reinstalss, all the bsods) the check the beryl forums. Google the link. There, start a thread with your exact specifications and i'm sure someone will help you out. :-)

---

### Post by tamagotono on 2006-11-04
> **noktekniq said:**
> so i spend countless hours reinstalling and formating ubuntu after so many failures of installing these 3d graphic desktop display. where can i get the best understandable guide which people can understand. 

i'm currently using nvidia 7800 with amd setup

Actually, setting up BERYL is really easy if you follow these directions and are running Edgy Eft.  Here is the link [http://forum.beryl-project.org/topic-5021-howto-beryl-aiglx-nvidia-drivers]("http://forum.beryl-project.org/topic-5021-howto-beryl-aiglx-nvidia-drivers")

If you are using dapper drake than it is a bit more difficult but just search the howto section on [www.beryl-project.org]("http://www.beryl-project.org") and I am sure you can find good directions on how to get it to work.  With the help of this site I was even able to get Beryl installed easially on my Dell laptop with a cheap i810 video chipset!

---

### Post by noktekniq on 2006-11-04
i tried that link from beryl forum and wasn't successful. maybe because i don't know anything about repositories and dont' know where to put the stuff. iono. but i guess i'll have to take a look at it again.

---

### Post by tamagotono on 2006-11-04
If you can't figure it out, I would recommend looking for a local Linux Users Group and attend their next meeting.  I live in Washington and am giving a small presentation on how to install beryl.  Most of the people in my group are familiar with Linux and are more than happy to help any noobies who attend and want to learn.  There is even a good chance that if you bring your computer they can help you during the meeting, but I would contact them first just to be sure.
  By the way, don't get too frustrated.  There is a steep learning curve when it comes to Linux but it is worth it.  Good Luck, and welcome to UBUNTU. :)

---

### Post by johnny9794 on 2006-11-04
> **noktekniq said:**
> i tried that link from beryl forum and wasn't successful. maybe because i don't know anything about repositories and dont' know where to put the stuff. iono. but i guess i'll have to take a look at it again.

Ok here is the starter guide for ubuntu 6.06.1 , second link is for adding repositories to ubuntu 6.06.1 .
[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)
[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories)

Here is the starter guide on Ubuntu edgy 6.10 and the second link is how to add repostories for ubuntu 6.10 .

[http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy)
[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_add_extra_repositories)

---

### Post by seuaniu on 2006-11-05
[Here's a guide for ya.]("http://doc.gwos.org/index.php/BerylOnEdgy")  

Folks are saying that you shouldn't try it... Well, I disagree.  Personally, I have fun learning new things, and screwing up and having to start over is a part of that, no matter what OS you use.

About the guide - when it says edit a file, a quick and dirty way to get that done is to do it from a terminal. You'll have one open anyway while following the guide.

```
sudo gedit /etc/x11/xorg.conf
```

Gedit is a graphical text editor which'll be easier to use, and 'sudo' is a command to run the next command (gedit) with admin priviliges.

Good luck!

---

### Post by chrisblue on 2006-11-05
Quick question from a newb. How can you edit files from the command line if you don't have the GUI running?

---

### Post by dpm on 2006-11-05
> **chrisblue said:**
> Quick question from a newb. How can you edit files from the command line if you don't have the GUI running?

There are many command line editors available. I guess the easiest to use for newbies is 'nano', which IIRC comes installed per default with ubuntu. To edit a file from the command line, just type:

```
nano  <name of the file you want to edit>
```Cheers

---

### Post by johnny9794 on 2006-11-05
> **noktekniq said:**
> so i spend countless hours reinstalling and formating ubuntu after so many failures of installing these 3d graphic desktop display. where can i get the best understandable guide which people can understand. 

i'm currently using nvidia 7800 with amd setup

I just installed this about couple hours ago, its working great, no problems yet but here is where you may start if you like.

[http://forum.beryl-project.org/topic-5021-howto-beryl-aiglx-nvidia-drivers](http://forum.beryl-project.org/topic-5021-howto-beryl-aiglx-nvidia-drivers)

---

### Post by noktekniq on 2006-11-05
i read that link about 3 times and tried once. failed the first time. i might try again when i have time.

---

### Post by johnny9794 on 2006-11-05
what is it that you are failing on? More details maybe someone or I maybe able to help. You running dapper 6.06.1 or edgy 6.10?

---

### Post by noktekniq on 2006-11-05
> **johnny9794 said:**
> what is it that you are failing on? More details maybe someone or I maybe able to help. You running dapper 6.06.1 or edgy 6.10?

[http://www.ubuntuforums.org/showthread.php?t=293768](http://www.ubuntuforums.org/showthread.php?t=293768)
had some problems posted in that link above. thanks

---

