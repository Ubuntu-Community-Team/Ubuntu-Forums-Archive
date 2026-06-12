---
title: "how do you make aboot partition?"
date: 2007-10-11
forum: General Help
---

### Post by Masterj15 on 2007-10-11
Since noone really helped me with my last post for this. I decied to make this more understandable.

All I want 

1# grub boot  (less than 2 g.b for bios to read ok)
2# file system
3# swap and all that other crap.


I hope someone can really help me this time. :(

---

### Post by be4truth on 2007-10-11
It is really hard to understand what you want. What crap you are talking about?

---

### Post by SuperDuck on 2007-10-11
Are you saying that you want a seperate partition for:

1) your "/boot" directory
2) your "/" directory for your OS
3) swap and other crap (please elaborate)

---

### Post by Masterj15 on 2007-10-11
> **be4truth said:**
> It is really hard to understand what you want. What crap you are talking about?

Damit..................ok....calm down masterjX9.

I can't get ubuntu to work beacuse of the error code 18 from grub. My stupid bios can't read the grub beacuse the hard drive is to big for the grub file to work. If I have a partion for the grub file. The bios will read the partion and allow the grub to work. So I'll try to explain this by percenatge.

100% =harddrive
10% =bios can read
97% = all my stuff
3% = swap file and other crap that comes with install

grub is storred on the 97% of my hard drive
the bios can only read up to 10%
making the grub come with an error code 18.

I need a partion of grub so that it would look like this
96% =all my stuff
3% = swap file and other crap that comes with install
1% =grub boot.

Now do people understand?

---

### Post by Masterj15 on 2007-10-11
> **SuperDuck said:**
> Are you saying that you want a seperate partition for:

1) your "/boot" directory
2) your "/" directory for your OS
3) swap and other crap (please elaborate)

YES, YES,YES,YES

Thank so much yes :) :) :)

how do you do it?

---

### Post by Masterj15 on 2007-10-11
I'm waiting at my manuel setup for SOMEONE TO HELP ME!

---

### Post by Masterj15 on 2007-10-11
WHY DOES ANYONE HELP ME IN ANY OF MY POSTS? THEIR ISN"T even a place to call for help. :(

---

### Post by Masterj15 on 2007-10-11
I GIVE UP! you people don't know anything! I thought this place was so that people can come to professionals! I've tried so much crap waiting for you people to post a freaking idea. you people make me take back the reason why I switched to ubuntu!

---

### Post by Shazaam on 2007-10-11
Since Ubuntu is FREE you have VOLUNTEERS helping you (most have a life) so help may take a while. If you would take the time to search and READ you may find what you need. Demanding help will get you ignored.

Try here...
[https://help.ubuntu.com/7.04/installation-guide/i386/](https://help.ubuntu.com/7.04/installation-guide/i386/)
and here...
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by Masterj15 on 2007-10-11
> **Shazaam said:**
> Since Ubuntu is FREE you have VOLUNTEERS helping you (most have a life) so help may take a while. If you would take the time to search and READ you may find what you need. Demanding help will get you ignored.

Try here...
[https://help.ubuntu.com/7.04/installation-guide/i386/](https://help.ubuntu.com/7.04/installation-guide/i386/)
and here...
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)


Try here...
[https://help.ubuntu.com/7.04/installation-guide/i386/](https://help.ubuntu.com/7.04/installation-guide/i386/)
and here...
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)[/QUOTE]

I alway read before I post. I read for hours on end before I even think about posting somthing. I this is where expert programmers are. Since I'm busy during the week [COLOR="Blue"](This is my day off)[/COLOR]
I have to get things done today or elese I'm screwd! When someone tell me to do something and I do it. I would think that people would tell me whats next to do in their list of instructions.

---

### Post by jocko on 2007-10-11
If you plan to do a fresh install of ubuntu, this should be quite easy.
In the partitioning part of the install process, make sure you select the option to set up your partitions manually (I don't remember exactly what the options are).
Set it up like this:

partition 1: 100 Mb should be enough to hold the grub configuration files and a fair number of kernels. Format as ext3, set the mount point to "/boot"

partition 2: Not sure how large it needs to be, I have it at 10 Gb, but its only about 40-50% full after installing ubuntu and all the extra apps I use.
Format it to ext3 and set the mount point to "/".

partition 3 (optional, but highly recommended): ext3, mount as "/home". You decide the size, this could take up the rest of the disk if you don't need more partitions.

More partitions or disks: set the mount points to "/media/whatever1", "/media/whatever2" etc. to get them to mount automatically on each boot.
If they are already formatted and contains files, make sure you do not let the installer format them.

---

### Post by Masterj15 on 2007-10-11
> **jocko said:**
> If you plan to do a fresh install of ubuntu, this should be quite easy.
In the partitioning part of the install process, make sure you select the option to set up your partitions manually (I don't remember exactly what the options are).
Set it up like this:

partition 1: 100 Mb should be enough to hold the grub configuration files and a fair number of kernels. Format as ext3, set the mount point to "/boot"

partition 2: Not sure how large it needs to be, I have it at 10 Gb, but its only about 40-50% full after installing ubuntu and all the extra apps I use.
Format it to ext3 and set the mount point to "/".

partition 3 (optional, but highly recommended): ext3, mount as "/home". You decide the size, this could take up the rest of the disk if you don't need more partitions.

More partitions or disks: set the mount points to "/media/whatever1", "/media/whatever2" etc. to get them to mount automatically on each boot.
If they are already formatted and contains files, make sure you do not let the installer format them.

omg. THANK YOU SO MUCH. FINALLY A GUINESS with a PLANNNNNN!!!!!!!:)

---

### Post by jocko on 2007-10-12
You're welcome!

---

### Post by SuperDuck on 2007-10-12
> **Masterj15 said:**
> I GIVE UP! you people don't know anything! I thought this place was so that people can come to professionals! I've tried so much crap waiting for you people to post a freaking idea. you people make me take back the reason why I switched to ubuntu!

Are you serious?  You're this pissed because someone didn't reply within 3 minutes of your original post?  I don't know about other people, but I posted while I was at work and, believe it or not, didn't have time to hang around to help you get your boot partition.  I was planning on checking on the thread later in the evening to see if you got your answer.  I see that you did - good for you.

If you want help in the future I suggest being less rude, more patient and a hell of a lot more respectful.  The Linux community is based on a DIY ethic that means not expecting someone to fix your problems for you, *especially* if you act like an *** towards the people you're trying to get help from.

---

### Post by jocko on 2007-10-12
> **SuperDuck said:**
> Are you serious?  You're this pissed because someone didn't reply within 3 minutes of your original post?  I don't know about other people, but I posted while I was at work and, believe it or not, didn't have time to hang around to help you get your boot partition.  I was planning on checking on the thread later in the evening to see if you got your answer.  I see that you did - good for you.

If you want help in the future I suggest being less rude, more patient and a hell of a lot more respectful.  The Linux community is based on a DIY ethic that means not expecting someone to fix your problems for you, *especially* if you act like an *** towards the people you're trying to get help from.

I agree... If I had read that rude post before I decided to help I may not have helped. It seems like some people don't seem to understand that most people that read these forums are just users themselves. (I'm not a computer/linux specialist, I'm a geneticist that use Ubuntu at home for fun and because I like the challenge of figuring out how things work. And of course because it's free and less bloated than Windows)
If someone decides to help, It's not because it's their job, but because they are just friendly and helpful and try to contribute to the community.
If MasterJ wants help in the future, he should try to explain the problem better and be more patient and polite.

---

### Post by Masterj15 on 2007-10-15
> **SuperDuck said:**
> Are you serious?  You're this pissed because someone didn't reply within 3 minutes of your original post?  I don't know about other people, but I posted while I was at work and, believe it or not, didn't have time to hang around to help you get your boot partition.  I was planning on checking on the thread later in the evening to see if you got your answer.  I see that you did - good for you.

If you want help in the future I suggest being less rude, more patient and a hell of a lot more respectful.  The Linux community is based on a DIY ethic that means not expecting someone to fix your problems for you, *especially* if you act like an *** towards the people you're trying to get help from.

> **jocko said:**
> I agree... If I had read that rude post before I decided to help I may not have helped. It seems like some people don't seem to understand that most people that read these forums are just users themselves. (I'm not a computer/linux specialist, I'm a geneticist that use Ubuntu at home for fun and because I like the challenge of figuring out how things work. And of course because it's free and less bloated than Windows)
If someone decides to help, It's not because it's their job, but because they are just friendly and helpful and try to contribute to the community.
If MasterJ wants help in the future, he should try to explain the problem better and be more patient and polite.

first: i'm not rude (My friend likes to make jokes. He doesn't know how to. I changed my password beacuse of him. This is why I wasn't here for some days, so I can see if changing the password would block him out.)

second:I'm patient with posts beacuse I know things don't get taken care of instantly. I usually wait until 2 days from the intital post.

---

