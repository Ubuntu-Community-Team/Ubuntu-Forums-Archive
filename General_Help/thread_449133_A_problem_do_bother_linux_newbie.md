---
title: "A problem do bother linux newbie"
date: 2007-05-19
forum: General Help
---

### Post by chunchengch on 2007-05-19
People, especially Linux newbies, post threads here to look for helps from others, fortunately we always can get what we need. However, some replies are too concise to understand by Linux newbie, and I do believe the most of threads are posted by newbies, we are not so familiar with Linux like we are with Windows, so what we need is a **step-by-step** solution, although it maybe annoying to Linux stagers.

For example, I always find replies like this ,,,

**run asoundconf-gtk** --- how to run?
**editing your /etc/X11/xorg.conf file**  --- how to edit?
**but to get beryl back to its original settings, you must delete the .beryl folder** --- how to get back? and where is the folder?

We frequently experience problems especially with needs of installing packages, plugins etc., a **step-by-step** instruction will be greatly helpful for rookies, because it is sometimes really hard to understand what README says.

---

### Post by raja on 2007-05-19
I am sure that such replies are in the minority. Most of the times, people give detailed replies or give commands that can be just copied and pasted into a terminal.
On the other hand, I would say that sometimes the one asking the questions poses a very incomplete question. Newbie or not, I would suggest that those asking for help should clearly state the problem and provide enough background information so that you can get a quick answer.

---

### Post by vtel57 on 2007-05-19
> **chunchengch said:**
> People, especially Linux newbies, post threads here to look for helps from others, fortunately we always can get what we need. However, some replies are too concise to understand by Linux newbie, and I do believe the most of threads are posted by newbies, we are not so familiar with Linux like we are with Windows, so what we need is a **step-by-step** solution, although it maybe annoying to Linux stagers.

For example, I always find replies like this ,,,

**run asoundconf-gtk** --- how to run?
**editing your /etc/X11/xorg.conf file**  --- how to edit?
**but to get beryl back to its original settings, you must delete the .beryl folder** --- how to get back? and where is the folder?

We frequently experience problems especially with needs of installing packages, plugins etc., a **step-by-step** instruction will be greatly helpful for rookies, because it is sometimes really hard to understand what README says.

We understand what you're saying here, Chunch. We were all new at this at one time. Sometimes we forget, though. :(

To answer your sample questions:

---> When someone tells you to "run" a command or program, they usually mean from within the Gnome (or Konsole in Kubuntu) Terminal, the graphic emulator of the command line (text only). So, for example... someone told you to run asoundconf-gtk. You would:

1) Open the Terminal program. It's in the Main Menu -->Accessories --> Terminal.

2) When the Terminal program opens, at the prompt, which will look like this:

> <username>@<domain_name>:~$

type "asoundconf-gtk" (without the quotes).

---> When someone says you need to edit your xorg.conf file, they mean that you need to make changes within the xorg.conf file, which is a configuration file that determines how X (the windows system used in Ubuntu) behaves. To edit that file, which is just a plain old text file, you can use a command line editor like Vi or Vim (advanced users) or you can edit using Gnome's neat little editor app called Gedit. To edit the xorg.conf using the graphic (Gedit) method:

1) Open the Terminal once again and type:

```
$ sudo gedit /etc/X11/xorg.conf
```

What this command is doing is telling Gedit to open the file "xorg.conf" in the X11 sub-directory of the /etc directory, using Root privileges (sudo = superuser do).

2) Manipulate the xorg.conf file however you need to, then click Save on Gedit. That's it. You're all done.

---> When someone tells you to remove a directory... first off, be very wary about removing things from your system. Anyway, a directory with a . in front of it is not displayed in normal mode within Nautilus (the Gnome File Manager). It is a "hidden" file. You must have "Show hidden files" checked in Nautilus' View menu to see them.

Most preference directories, like .beryl, are going to be located in your own directory... your personal directory created when your user account was created. That would be /home/<your_username>. To delete the directory, just RIGHT click on it and "Move to trash". It's that simple.

Hope these explanations have helped you a bit. Don't forget, though, it's ultimately the user's responsibility to learn for themselves. We are all users here, just like you. We volunteer our time helping folks because we want to "give a little back" to the community that helped us in the beginning, and also because quite often we learn by teaching.

Enjoy your GNU/Linux experience, and remember... it gets a lot easier once you know everything. ;)

---

### Post by noerrorsfound on 2007-05-19
If they tell you to do something and you don't know how, ask them how to do it. People don't always give an extremely detailed tutorial on how to do basic things, because if the person already knows how to do things such as open the terminal then it's just a waste of time that could be spent answering more questions.

---

### Post by Bachstelze on 2007-05-20
> **chunchengch said:**
> a **step-by-step** instruction will be greatly helpful for rookies

There is an **Absolute Beginner** forum for that. No offence meant but someone who doesn't know how to edit a file should rather pst there.

---

### Post by chunchengch on 2007-05-20
I am a Chinese in Taiwan, so maybe I did not describe the problem correctly and properly in English, however I just want to point out a difficult situation what a Linux newbie will face when they experience problems in using Linux, I just posted a thread about how to playing APE audio in Linux "**Personal summary of playing APE audio with Beep Media Player**", you will find out what I mentioned in this thread. Thanks.

---

