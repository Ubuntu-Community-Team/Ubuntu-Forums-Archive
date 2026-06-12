---
title: "Programs Working Dir"
date: 2019-11-05
forum: General Help
---

### Post by simone-truglia on 2019-11-05
Hi guys, 

i'd like to know if there is a way to find all the files used by a specific program.

Just for example: i've downloaded Telegram for the official site, and there are only two files (Telegram and Update). 

When I start Telegram fort he first time, I set up my number in order to use my account.

Now, every time I open Telegram, my account is already there, so there is a folder with all these information saved in it.

So, I would like to find all the files used by a program.

But I would like to know if there is a general way, not only the directories where Telegram saves its files, but a way to know for each program I want where it saves its files.


There is also another related question...

I would like to use more than one account for Telegram. In windows 7 it was really easy, I just needed to duplicate the Telegram folder in Program Dir in order to have different instances using different data directories.

In Ubuntu I've no idea how to do that. Becasue:

1. I dont' know where Telegram saves its files

2. I dont' know how to ask Telegram to save its files in a specific directory


So, in general, I'd like to know if there is a way to ask a specific program to use a specific data directory to save its file and do not use the defaul one.

In this way, I could use two different instances of Telegram, specifying them to salve data in different places.

Anyway I used the Telegram example, but I'd like to know if there is a general way to to these :)


Really sorry for my English, I'm working on it

---

### Post by TheFu on 2019-11-05
TL;DR .... **lsof**  From the manpage:
```
DESCRIPTION
       Lsof  revision 4.89 lists on its standard output file information about
       files opened by processes
```

I've never used Telegram.  Prefer to run my own chat, voice, video conference server.

1 question per thread, please.

---

### Post by Holger_Gehrke on 2019-11-05
Programs on Ubuntu generally run with the rights of the user starting the program, so Telegram can only put its files where you could put files, mainly in your home directory, on external media that where plugged in during your session and in /tmp. The latter is meant for temporary files and there's no guarantee that they wouldn't get erased after session's end; the exact name of the mount points for external media are unpredictable for the author of an application; so some (probably hidden) directory or file in your $HOME is the place to look.

So to find out where Telegram puts its files I first created a list of all files in my $HOME ('find ~ >/tmp/filelist.txt' in a terminal), installed Telegram, ran it, exited it completely and created a second list of files ('find ~ >/tmp/filelist2.txt'). Then I compared the two files using 'diff /tmp/filelist.txt /tmp/filelist2.txt' and found '~/.local/share/TelegramDesktop/'. If that method hadn't given any usable results I would have looked in the various systems for storing configuration information (dconf, gconf, xfconf) that I have running (there would probably have been files created if the data was stored in one of those, but the names of those files would probably not have told me what program they belonged to).

As for using different accounts in Telegram: there's an option ('Hamburger'-menu, Settings, 'three vertical dots', log out) to log out of an account. You can then enter a different phone number and get sent a new login code (as a message on the phone). So it should be possible to have different accounts on one installation without switching out the directory with the data.

Holger

---

### Post by simone-truglia on 2019-11-05
Oh thank you for you suggest guys.

Thanks for your suggestes [**[COLOR=#000000]Holger_Gehrke[/COLOR]**]("https://ubuntuforums.org/member.php?u=1961578")


So, there is no way to force a program to use a specific directory for datas?

---

### Post by TheFu on 2019-11-05
> **simone-truglia said:**
> Oh thank you for you suggest guys.

Thanks for your suggestes [**[COLOR=#000000]Holger_Gehrke[/COLOR]**]("https://ubuntuforums.org/member.php?u=1961578")


So, there is no way to force a program to use a specific directory for datas?

It depends on the program.  config options, environment variables, just depends on the programming team whether they decided to follow normal development practices.

Of course, you can always use symbolic links to redirect the actual storage used for any directory.  This is usually a short-term solution.

---

### Post by Holger_Gehrke on 2019-11-05
How about simply creating a second user account in Ubuntu ? You could then [switch back and forth between the two users]("https://help.ubuntu.com/lts/ubuntu-help/shell-exit.html"), each with it's own Telegram with its own data.

Holger

---

### Post by linuxenthusiast on 2019-11-09
I don't know if it can help but you can also know which files and directories are created when you installed a specific package on your server.

> [COLOR=#242729][FONT=Consolas]dpkg-query -L <package_name>[/FONT][/COLOR]

It won't tell you which files are ACTUALLY being used but it can tell you where files are located.

---

### Post by Holger_Gehrke on 2019-11-09
@linuxenthusiast: great idea if it were a Debian package, but it isn't (although telegram is available from the repositories; the version there is rather old for 18.04, but the one for 19.10 is close to current; there's also a snap ...).
But simone-truglia downloaded it from the official site and the archive contains just two binaries. And anyway the files of interest in this case aren't the files installed but the ones created by the program at run-time to store credentials and settings.

@simone-truglia: As far as I can tell, Telegram doesn't accept any command line parameters and options at all. Calling it with various standard option didn't get any reaction and looking through 'strings Telegram' showed a lot of interesting stuff, but nothing that looked like accepted options. But I did manage to have it run as another user and have two Telegram sessions open at the same time. What I did was to create a second User named 'second', allow that user to access the X-Display by running 'xhost +local:' and then run 'sudo -u second -H ./Telegram'. After entering my password and waiting a while for Telegram to do it's setup in the second account, it began giving errors about not being able to access the sound system and finally brought up it's welcome screen without a configured account. So as long as one only wants to do text chat, it is possible to have two instances of telegram open at the same time for different accounts. It might be possible to configure sudo to work without a password for this particular situation and to configure the sound system to accept a connection from a program running under a different user, but I haven't really tried ...

Holger

---

### Post by TheFu on 2019-11-09
> **Holger_Gehrke said:**
>  It might be possible to configure sudo to work without a password for this particular situation and to configure the sound system to accept a connection from a program running under a different user, but I haven't really tried ...

Holger

Definitely possible through the /etc/sudoers.d/     Something like:
```
first localhost = (second) NOPASSWD: /path/to/Telegram
```
Then I'd make an alias so running it is easy.
```
alias 2ndtgram='sudo -u second -H /path/to/Telegram'
```

There are other techniques. I didn't test the sudoer line. Breaking the sudoers file(s), can lead to a system where nobody has sudo abilities.  I did that a few weeks ago. Had to hack in using recovery mode to fix it.

---

