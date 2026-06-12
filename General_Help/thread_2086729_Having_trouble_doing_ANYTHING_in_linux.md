---
title: "Having trouble doing ANYTHING in linux"
date: 2012-11-21
forum: General Help
---

### Post by krai havok on 2012-11-21
OK so I just jumped right into linux and have been trying for the past 4 days straight to do something ... anything in this and I cant even do the simplest thing that I could do in windows. I dont know what to do!!!

I try to copy paste, I dont have permission
I look for a way to get root to get permission it doesnt work (gksudo nautilus as well as other commands)
I try to do it command line (cp place to place) and either what I am copying doesnt exist or the place i am telling it to go doesnt exist
cant download themes and when I do dont know what to do with them
same with screen savers

I knew this wasnt going to be easy I just didnt think it was going to be impossible ...

Im sorry I am just really frustrated and have no idea where to turn. I have posted on about 4 different forums (with very speciffic problems) with no luck answers, as well as went to the linux mint irc help room. 

Is there anyone that can help me - tutorial, how to ... something ... 

thank you

---

### Post by snowpine on 2012-11-21
Be patient, learning Linux is a lengthy process. :)

Most files you'll have to deal with on a daily basis, are in your /home folder, therefore there is no reason to use sudo/gksu. What is the specific file you want to copy, from where and to where, and why?

Please be specific with your questions and we'll do our best to help. You may want to create a separate thread for each question, with a descriptive thread title.

The best tutorials are found at:

[http://help.ubuntu.com](http://help.ubuntu.com)
[http://wiki.ubuntu.com](http://wiki.ubuntu.com)
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

and of course these forums. :)

---

### Post by JC Cheloven on 2012-11-21
Hi, you should indeed be able to copy, paste, and such, without the need ofroot privileges, which you should also be able to get if you wish. For example, can you use sudo from terminal?

Anyway, this all sounds to me as an incorrect install. Perhaps due to a faulty download, or CD writing. Did you ckeck the MD5sum?

BTW: I've seen you have posts back from 2008, but you didn't post any of those specific problems you mention here, at ubuntu forums. Perhaps being more specific could help us. 

Greetings.

---

### Post by QIII on 2012-11-21
I'm not sure I'd go cutting and pasting into files you need elevated privileges for at this point anyway...

---

### Post by krai havok on 2012-11-21
Gentlemen, 

thank you so much for your responses. 

I would like to appologize for my origonal message, its typo's and the general way it sounded. I was frustrated, because I dove head first into Linux with no way back to Windows, but felt I had no way forward either. I know that this is not the case but that's how it felt. I do feel better now that someone has answered me, so thank you again. 

QIII - I am pretty sure you are right, but whenever I was trying to move a theme I had downloaded (copy paste) to the theme folder (/home/usr/shar/themes i think) telling me permission denied. Thats why I was trying to get root

JC Cheloven - perhaps it is a correct install. How do you go about checking the MD5?

snowpine - Thank you for the kind encouraging wods sir. Of course you are right, it takes time. I just feel that since I have been working with Linux on and off (not professionally but in my spare time) I should know more than I do. I think I am more angry at myself for not knowing more that's all. 

I was trying to download themes (just to see if I could do something simple) and when what I downloaded (from gnome-look on the web) was done, I found a tutorial(s) that said it should be copied to the themes folder, but I was denied. I tried both command line and copy paste and neither worked.

---

### Post by snowpine on 2012-11-21
I believe you can make a themes folder in your home folder, then you can copy & paste to it as your user without using sudo.

The reason your copy failed by the way was a typo. Instead of:

```
/home/usr/shar/themes
```

the correct folder is 

```
/usr/share/themes
```

**Typos in 'sudo' commands can ruin your system!** Always triple-check any terminal commands you are executing with 'sudo' and when in doubt come to the forums for advice before proceeding.

---

