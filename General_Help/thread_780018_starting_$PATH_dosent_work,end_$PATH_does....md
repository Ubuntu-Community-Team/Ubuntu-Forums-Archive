---
title: "starting $PATH dosent work,end $PATH does..."
date: 2008-05-03
forum: General Help
---

### Post by of_darkness on 2008-05-03
Now im trying to get my /opt/apps/ folder to be a starting $PATH.
```
PATH=$PATH:/opt/:$PATH 
export PATH 
``` dosent make bash look in > /opt/apps/beediff/beediff cause > beediff dosent show upp as a valid comand in bash when > bee*tab* as it would if > /opt/apps/beediff where in my PATH.

I have done a workaround untill now whith > PATH=$PATH:/opt/scripts and 2line bash scipts point to my compiled apps in /opt/apps/ but now i want 2 have opt as starting PATH.

and i made my workaround like this as i found on the net:
> in .bashrc , /etc/bash.bashrc and /etc/X11/Xsession.d/55blutengel_env```
# Add Blutengel's environment variables
. /etc/blutengel_env
```and > in /etc/blutengel_env ```
# Blutengels's environment variables.
# Sourced by:
# /etc/bash.bashrc (for interactive non-login shells)
# /etc/X11/Xsession.d/55blutengel_env (for Xsessions)

PATH=$PATH:/opt/apps/bin
PATH=$PATH:/opt/scripts/
PATH=$PATH:/opt/
PATH=$PATH:/usr/lib/kde4/bin
```

system is Kubuntu Hardy 64bit and kde 3* konsole as terminal frontend and bash as shell in Konsole

---

### Post by chrisccoulson on 2008-05-03
If you want to add extra search paths to $PATH, then append them to the 'PATH=' line in /etc/environment, separated by colons. Log out and back in for it to take effect. 

That's the easiest way;)

---

### Post by of_darkness on 2008-05-03
> **chrisccoulson said:**
> If you want to add extra search paths to $PATH, then append them to the 'PATH=' line in /etc/environment, separated by colons. Log out and back in for it to take effect. 

That's the easiest way;)
Hmm shall try it:) but it dosent change the wierd behaviur of path, cause starting path should work not just end path..

---

### Post by chrisccoulson on 2008-05-03
I'm not really sure what you mean by 'starting path should work not just end path'. What do you mean by 'starting path' and 'end path'?

---

### Post by of_darkness on 2008-05-03
> **chrisccoulson said:**
> I'm not really sure what you mean by 'starting path should work not just end path'. What do you mean by 'starting path' and 'end path'?
End path is PATH=$PATH:/usr/bin and no dirs under /usr/bin is int the path
Starting path is PATH=$PATH:/usr/stuff/old-stuff/my-stuff/applications:$PATH and path then starts at applications and all dirs underneath like application/2008/05/27/firefox/ is in the path but my-stuff is not in the path.

This is what i gatterd by testing and reding about path..

---

### Post by chrisccoulson on 2008-05-03
$PATH just contains a list of directories that are searched by the shell when you run a command. If the command isn't in any of the directories specified in $PATH, then the shell spits out an error.

The only difference between 'PATH=$PATH:/usr/local/bin' and 'PATH=/usr/local/bin:$PATH' (assuming $PATH=/bin:/usr/bin) is that '/usr/local/bin' ends up at the end of the PATH in the first case and the start of it in the second case. AFAIK, this only affects the order in which the directories are searched.

---

### Post by of_darkness on 2008-05-03
well a end path - PATH=$PATH:/opt don't include /opt/scripts or /opt/apps/aplication-name/aplication-executable-file ```
[ blutengel: ~ ]$ be
beagle-build-index           beagled-shutdown             beagle-index-info            beagle-ping                  beagle-shutdown              beep-media-player
beagle-config                beagle-dump-index            beagle-info                  beagle-query                 beagle-status                beep-media-player-2
beagled                      beagle-extract-content       beagle-manage-index          beagle-search                beast                        beforelight
beagle-doc-extractor         beagle-imlogviewer           beagle-master-delete-button  beagle-settings              beast-0.7.1
[ blutengel: ~ ]$ be
 
``````
[ blutengel: ~ ]$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/home/blutengel/bin:/opt/:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/home/blutengel/bin:/usr/lib/kde4/bin:/opt/:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/home/blutengel/bin:/opt/:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin:/home/blutengel/bin:/usr/lib/kde4/bin
[ blutengel: ~ ]$
``` ```
[ blutengel: ~ ]$ ls -l /opt/apps/beediff/beediff
-rwxr-xr-x 1 blutengel blutengel 295672 2008-05-03 12:02 /opt/apps/beediff/beediff
[ blutengel: ~ ]$
```So the thing i want do do is get /opt/apps in path and > [ blutengel: ~ ]$ ls -d /opt/apps/
21051-splash/                                     GPL.txt                                           NetfilterStatsBuilder/
37074-knamer0.10/                                 GutenMark_LinuxIntel_20020714/                    ondesklogs/
53687-pacpl-ki-1.0.2/                             historic.log                                      onekript-0.7.2/
5804-md5sha1calc-0.5/                             indywiki-0.9.4/                                   PasteClipboard/
60864-youtubedownloader/                          kavi2dvd/                                         piecrypt-0.1/
68923-On-Desktop-Logs/                            Kernel/                                           realplayer/
70782-59947-Stixiv1_2/                            kommander-apps/                                   Realplayer/
beediff/                                          konqueror_kopete.pl                               rssowl_1_2_4_linux_64/
bin/                                              kouvert.0.3/                                      scripts/
checkgmail-1.13/                                  kpsql-0.2/                                        Sudden Strike II/
checkgmail-1.13.tar.bz2                           KSplasher/                                        themis-1.0-RC1/
checkgmail.old.tar                                Kuten-0.1/                                        thunderbird/
crontab/                                          languages/                                        windows-apps/
downloads/                                        manslide-2.0.3/                                   xVideoServiceThief_1_8_2_alpha_dynamic_linux_bin/
Email_files_with_thunderbird_adding_details/      md5Calc/                                          yakuake_open_session/
Freenet/                                          MyJSQLView/                                       yakuake_open_session.pl
[ blutengel: ~ ]$  them and therir exacutables in my path so that i just can start them by entering their exacutables names. or in some cases whith python or java prefix.. and not have to give path in comand.

---

### Post by of_darkness on 2008-05-03
> **chrisccoulson said:**
> I'm not really sure what you mean by 'starting path should work not just end path'. What do you mean by 'starting path' and 'end path'?

 The thing about starting/begning and end path is taken from [http://www.troubleshooters.com/linux/prepostpath.htm](http://www.troubleshooters.com/linux/prepostpath.htm) > **Pre and Post Pathing**

 Linux determines the executable search path with the $PATH environment variable. To add directory /data/myscripts to the beginning of the $PATH environment variable, use the following:
 
  PATH=/data/myscripts:$PATH
 To add that directory to the end of the path, use the following command:
 PATH=$PATH:/data/myscripts

---

### Post by Dr Small on 2008-05-03
I always simply use:
```
PATH=:/path/to/new/:$PATH
```

---

### Post by of_darkness on 2008-05-03
> **Dr Small said:**
> I always simply use:
```
PATH=:/path/to/new/:$PATH
```

Hmm tried it in a Konsole session(pasting PATH=:/opt/apps/:$PATH and then running export PATH but nopp then i apended it in /etc/blutengel_env and saved and then started a new konsole shell but nopp.. and blutengel_env works i tied to cut away the /opt/scripts jsut to test and then no beediff-13 as i renamed my 1liner starting script.. and ofc no beediff..

---

### Post by Dr Small on 2008-05-03
Try:
```
PATH=:/opt/apps/:$PATH
echo $PATH
```

And see what it does.
If that doesn't work, then try closing the terminal, open a new one:
```
export PATH=:/opt/apps/:$PATH
echo $PATH
```

---

### Post by of_darkness on 2008-05-03
well now it appers in path listng but still it dosent inclued /opt/apps/beediff/beediff and i also tried it in gnome terminal.. and i have a some programs running in some of the sessions of konsole so i cant shut konsole down but gnome-teminal i could.. but i can hardly se that i would affect how bash interprets path.. or is it just that it does?.. sound to me wery strange if it does.. cause other paths i can set but only ending paths

---

### Post by chrisccoulson on 2008-05-04
You need to specify each individual directory in the PATH environment variable. The shell only looks in the specified folders, and not in subfolders.

I think you've got a bit confused about the pre and post-pathing terminology in that page you linked. The only difference between the two examples given (pre-path and post-path) is the search order of the folders (someone please correct me if I'm wrong here)

If you want to add folders to PATH, then the best way is to append them to the end of the 'PATH=' line in /etc/environment, like I said earlier. This file will get sourced by every shell you use, so it will work from anywhere. You'll have to specify subfolders individually though, which looks like your PATH environment variable is going to be pretty long. This will probably slow down searches on the shell, and is why we have executables located only in a small number of folders (/bin, /sbin, /usr/bin, /usr/sbin etc)

---

### Post by of_darkness on 2008-05-04
> **chrisccoulson said:**
> You need to specify each individual directory in the PATH environment variable. The shell only looks in the specified folders, and not in subfolders.

I think you've got a bit confused about the pre and post-pathing terminology in that page you linked. The only difference between the two examples given (pre-path and post-path) is the search order of the folders (someone please correct me if I'm wrong here)

If you want to add folders to PATH, then the best way is to append them to the end of the 'PATH=' line in /etc/environment, like I said earlier. This file will get sourced by every shell you use, so it will work from anywhere. You'll have to specify subfolders individually though, which looks like your PATH environment variable is going to be pretty long. This will probably slow down searches on the shell, and is why we have executables located only in a small number of folders (/bin, /sbin, /usr/bin, /usr/sbin etc)
Mmm the thing was that i had always thougt it was recursive.. that wy i couldnt for the love of god understand wy it wouldent work..  Mmm now i have to come upp with some smart script that can symlink at the same time as i move the dir from my untarred dir where i compile/check stuff grabbed from the opendesktop webbsites..  cause as you said adding to path would be bad..

---

### Post by of_darkness on 2008-05-04
> **chrisccoulson said:**
> You need to specify each individual directory in the PATH environment variable. The shell only looks in the specified folders, and not in subfolders.

I think you've got a bit confused about the pre and post-pathing terminology in that page you linked. The only difference between the two examples given (pre-path and post-path) is the search order of the folders (someone please correct me if I'm wrong here)

If you want to add folders to PATH, then the best way is to append them to the end of the 'PATH=' line in /etc/environment, like I said earlier. This file will get sourced by every shell you use, so it will work from anywhere. You'll have to specify subfolders individually though, which looks like your PATH environment variable is going to be pretty long. This will probably slow down searches on the shell, and is why we have executables located only in a small number of folders (/bin, /sbin, /usr/bin, /usr/sbin etc)
and your are right about begging/end path as i locked into my path i found /opt/apps in the begging of path statement..:)

---

