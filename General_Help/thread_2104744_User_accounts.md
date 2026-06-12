---
title: "User accounts"
date: 2013-01-14
forum: General Help
---

### Post by grim3271 on 2013-01-14
Soo i activated my root account and now instead of the normal log on i write root and my password and just log in every time. i 've been like that for just about 3 month. but now i started running into many programs that won't run as root. but i tried logging into my normal account. but all the customizations were gone. it was just classic ubuntu. i used ubuntu tweak and alot programs to make ubuntu the way i love it so is there anyway to take all the stuff i made here and put it into the main account. so i have a root account and a no root account and booth are simply the same? thanks

---

### Post by ljmhk on 2013-01-14
Hi grim3271,

A lot of the user specific modifications will usually live in the user space, for example the bash profile is stored in the user directory under the name .bash_profile.

In theory if you duplicate any preference files from the /root/ home directory to the user home directory /home/$USER those preferences should be honoured on your next login/boot.

Where those preferences are saved is bound to be application specific so you might find not everything can be moved over without some digging around for the files.

---

### Post by audunpoi on 2013-01-14
I guess you would have to chown the files to your user after moving them.

---

### Post by grim3271 on 2013-01-14
iDK. i just want EVERYTHING i done here to be on a root and a non root account. or a command in the terminal to do the job. this is just for running POL ( play on linux) if you guys know how to run it as root it 'd be appreciated
POL is the only program capable of running a game i really love multiple sites say that only POL was able to run it

when i went to a non root acc. nothing i have here was there. not even files

or even a command in the terminal to make my root account open a program like a normal user.

JUST ANY WAY TO RUN POL with or without root capabilities

---

### Post by zombifier25 on 2013-01-14
Tough luck getting help if you log in as root.

Try creating a new user.

---

### Post by Impavidus on 2013-01-14
To get you started on a normal account, log in as root for the last time and copy all your settings and data:```
cp -R /root/* /home/yourusername/
chown -R yourusername:yourusername /home/yourusername/*
```I can't guarantee that everything will work, but most of it will. Then log off and log in on your normal account.

There is a reason why the root account is locked by default. If you insist on using the root account for normal activities you probably won't get much help on these fora.

---

### Post by mörgæs on 2013-01-14
To avoid future problems:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by grim3271 on 2013-01-14
That's the problem omg. that new profile will be like the default ubuntu with not even a single file
EDIT. wow this forum is pretty weird before i post this comment i only saw zombifier reply. once i commented i saw the last 2 replies

---

### Post by grim3271 on 2013-01-14
My main user account/NOT ROOT ONE
is named Ionized

So that means

cp -R /root/* /home/Ionized/
chown -R Ionized:Ionized /home/Ionized/*

When i write


cp -R /root/* /home/Ionized/ 
i get
cp: target `/home/Ionized/' is not a directory
chown: invalid user: `Ionized:Ionized'


and when i copy the entire thing i get something similar to this
chown: invalid user: `Ionized:Ionized'

---

### Post by ljmhk on 2013-01-14
remember its case sensitive, is it an "i" or an "I"?

As your root user have a look in the home directory:

ls -l /home

Do you see your user listed? If so then use the exact same folder name you see listed in your copy command and chown commands. 

basically the error is saying that username doesn't exist on the system.

---

### Post by haqking on 2013-01-14
it is the inability to use or understand Linux why it is not recommended to login as root.

Read [ROOTSUDO ]("https://help.ubuntu.com/community/RootSudo")as mentioned before.

---

### Post by grim3271 on 2013-01-14
It is Ionized with caps lock at the first letter.
Also i see no folder named Ionized in home.. what do i do?

---

### Post by sandyd on 2013-01-14
> **grim3271 said:**
> It is Ionized with caps lock at the first letter.
Also i see no folder named Ionized in home.. what do i do?

Do you see any folders at all in /home ?
```

ls /home
```
Check if your user account exists on the system:
```

cat /etc/passwd | awk -F":" '{print $1}'

```
If it is not in the list, then you don't have an account other than root on the system.

---

### Post by grim3271 on 2013-01-14
Thanks i found it. when i did the command. and got into my account. it was just more like it in.. like 70 pct. the unimportant 70 pct :( the important 30 pct. was lost. am now on root again. anyone tell me how to run play on linux as root. i just want to run a single game :(

---

### Post by Impavidus on 2013-01-14
As far as I can tell you, it seems that somewhere in the Play on Linux's startup script there's the statement```

if user=root
    exit

```This is a security measure. PoL can run windows programs and therefore all windows malware. Giving those programs root access is dangerous. Even more dangerous than routinely using your system as root.

---

### Post by matt_symes on 2013-01-14
Without being rude, there is a lesson here.

I backup Windows AND Linux.

Please, please do the same.

---

### Post by grim3271 on 2013-01-14
> **Impavidus said:**
> As far as I can tell you, it seems that somewhere in the Play on Linux's startup script there's the statement```

if user=root
    exit

```This is a security measure. PoL can run windows programs and therefore all windows malware. Giving those programs root access is dangerous. Even more dangerous than routinely using your system as root.

I Bet usr/share/playonlinux/playonlinux double click that and display is the startup script. but there is no user=root there.

---

### Post by grim3271 on 2013-01-15
The title says it all..
I only want to run 1 game. that more than 1 website say that only playonlinux or POL can run it.

---

### Post by Elfy on 2013-01-15
*Thread moved to **Wine**.*

Not sure that running as root would be very sensible.

---

### Post by sffvba[e0rt on 2013-01-15
From [http://www.catb.org/esr/faqs/smart-questions.html#goal](http://www.catb.org/esr/faqs/smart-questions.html#goal)

> Describe the goal, not the step

If you are trying to find out how to do something (as opposed to reporting a bug), begin by describing the goal. Only then describe the particular step towards it that you are blocked on.

Often, people who need technical help have a high-level goal in mind and get stuck on what they think is one particular path towards the goal. They come for help with the step, but don't realize that the path is wrong. It can take substantial effort to get past this.

Stupid:
How do I get the color-picker on the FooDraw program to take a hexadecimal RGB value?

Smart:
I'm trying to replace the color table on an image with values of my choosing. Right now the only way I can see to do this is by editing each table slot, but I can't get FooDraw's color picker to take a hexadecimal RGB value.

The second version of the question is smart. It allows an answer that suggests a tool better suited to the task.


404

---

### Post by grim3271 on 2013-01-15
I want to run conquer online and several websites said that  only POL can run it. so i am now on root and taking all the stuff i made on root to a normal account did not work so now i must run POL as root i understand the risk. I am going to use that program 1 time tho -_- so please give me a way to run POL as root so i get conquer?

---

### Post by zombifier25 on 2013-01-15
> **grim3271 said:**
> Thanks i found it. when i did the command. and got into my account. it was just more like it in.. like 70 pct. the unimportant 70 pct :( the important 30 pct. was lost. am now on root again. anyone tell me how to run play on linux as root. i just want to run a single game :(

You're still logged as root?

Please stop. Running as root poses a lot of security and usability problems. That's why root is disabled by default in Ubuntu, and this forum has a policy on not supporting setups that has root enabled.

---

### Post by grim3271 on 2013-01-15
Please anyone reply D:

---

### Post by sffvba[e0rt on 2013-01-15
Please refrain from bumping your thread more than once every 24 hours.



404

---

### Post by grim3271 on 2013-01-15
What in the world is bumping your thread? please answer dude D:...

---

### Post by Toz on 2013-01-15
Bumping is when you re-post a request for help within a 24-hour period when no-one has replied (this would be your post #5). This forum is comprised of volunteers from around the world, all in different time zones with different work/life responsibilities. We respectfully ask that people not "bump" their posts (requests for help) more than once in a 24 hour period.

That being said, the advice that @elfy gave in post #2 is good advice - you should not be running POL as root.

> so i am now on root and taking all the stuff i made on root to a normal account did not work
Are you saying that you tried this with a normal account and it didn't work? Can you provide more details about what you did, what didn't work and any error messages you received? That would be more helpful.

As for HOWTOs, have you seen the following two links:
- [Wine App DB HowTo]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4055")
- [PlayOnLinux Custom Script]("http://www.playonlinux.com/en/topic-1552-Conquer_Online_20.html")

---

### Post by haqking on 2013-01-15
> **Toz said:**
> 


Are you saying that you tried this with a normal account and it didn't work? Can you provide more details about what you did, what didn't work and any error messages you received? That would be more helpful.

As for HOWTOs, have you seen the following two links:
- [Wine App DB HowTo]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=4055")
- [PlayOnLinux Custom Script]("http://www.playonlinux.com/en/topic-1552-Conquer_Online_20.html")

The OP other thread is here [http://ubuntuforums.org/showthread.php?t=2104744](http://ubuntuforums.org/showthread.php?t=2104744)

---

### Post by sffvba[e0rt on 2013-01-15
As has been stated running POL as root is not a good idea, and as has also been stated in your other thread running as root is bad and not recommended.

As both threads are seemingly serving the same purpose I am **closing **this one.  Listen to the advice given in the other thread, or stop asking for it.


404

---

