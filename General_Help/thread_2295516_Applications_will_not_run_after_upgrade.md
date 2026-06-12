---
title: "Applications will not run after upgrade"
date: 2015-09-19
forum: General Help
---

### Post by uaebuntu on 2015-09-19
Using 64 bit Ubuntu 15.04 

Had a single SSd on my son's games machine, but we were always running out of space so I added a 1TB HDD mounted at /home and reinstalled Ubuntu on the SSD. installed all the system software as me including Steam and Java

I created my son's username so we now have two directories on the HDD. Did a restore of my son's home directory and everything looked OK until he tried to run applications from his directory.

Steam seems to be missing some 32 bit libraries, and thinks we are short on disk space, dies with fatal error
Minecraft can't find Java to run with

So I guess things that were archived on the single SSD version, then restored to the two disk version are missing some link to the libraries and applications

Any suggestions?

Jim

---

### Post by TheFu on 2015-09-19
Please post the exact, copy/paste, errors as run from a terminal for each program.  I suspect his account is just missing a few environment variables that yours got "somehow".

BTW, you could have just mirrored the files from the original install over to the new disk - as long as the files and directories are mounted to the expected locations, with Unix file systems (not NTFS), Unix doesn't care.

---

### Post by uaebuntu on 2015-09-20
[ATTACH=CONFIG]264545[/ATTACH][ATTACH=CONFIG]264546[/ATTACH][ATTACH=CONFIG]264547[/ATTACH][ATTACH=CONFIG]264548[/ATTACH][ATTACH=CONFIG]264545[/ATTACH][ATTACH=CONFIG]264546[/ATTACH][ATTACH=CONFIG]264547[/ATTACH][ATTACH=CONFIG]264548[/ATTACH][ATTACH=CONFIG]264545[/ATTACH][ATTACH=CONFIG]264546[/ATTACH][ATTACH=CONFIG]264547[/ATTACH][ATTACH=CONFIG]264548[/ATTACH]

Thanks for the reply. I have attached the screen shots of what's happening when I try and run steam.

First it is concerned that I don't have enough disk space, however the 128 GB SSD only has the Linux foot print and the 1TB HDD only has my son's directory.

Then it tells me about the missing 32 bit libraries

---

### Post by uaebuntu on 2015-09-21
Sorry about the mess when adding the screen shots.

Partially solved the problem... I believe Steam only runs on 32bit Ubuntu I had installed 64 bit as per my other machines, hence the problem with missing i386 libraries.

I've partitioned the SSD disk in half and loaded a 32 bit version of 15.04 in one partition and 64bit in the other The 1TB HDD is mounted at /home on both versions.

Still having some issues with steam, see screen shot

[ATTACH=CONFIG]264563[/ATTACH]

and it thinks I am low on disk space but there is 50GB free on the SSD and the best part of 1TB on the HDD

Jim

---

### Post by TheFu on 2015-09-21
Screen shots are to be avoided. copy/paste the TEXT only here. Think of all the people who pay by the byte for internet.  Plus, I can't copy/paste from your post and fix the issue.  This isn't Windows. We don't need/want screen shots 99.9999999999% of the time.

---

### Post by uaebuntu on 2015-09-21
Apologies for the screenshots.

The only error message I am getting now is the Steam one which says

"Couldn't set up Steam runtime. Are you running low on disk space? Continuing...."

but nothing happens.

---

### Post by ian-weisser on 2015-09-21
> **uaebuntu said:**
> "Couldn't set up Steam runtime. Are you running low on disk space? Continuing...."

To determine if you are truly low on disk space, please show us the output from the following two commands. (TheFu is right, use copy/paste [URL="http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168"]and ```
 tags[/URL])
[code]df
df -i
```

---

### Post by TheFu on 2015-09-21
There are 32-bit compatibility libraries for x64 systems. But since I don't game and don't use steam, I don't know whether that matters or not.  I would use a good web search for "install steam x64 ubuntu 14.04" to see if someone from a reputable website hasn't already solved this.

[https://askubuntu.com/questions/257084/how-do-i-install-steam-on-a-64bit-system](https://askubuntu.com/questions/257084/how-do-i-install-steam-on-a-64bit-system) is a top result.

I don't run 15.04. Support ends in a few months and I don't have time to reinstall an OS every 6 months like the non-LTS releases require.  14.04 is the current LTS release with 5 yrs of support.

---

### Post by uaebuntu on 2015-09-22
Thanks. I have copied the outputs below..

```
jim@jim-X8ST3:~$ df
Filesystem                                  1K-blocks       Used                Available           Use%     Mounted on
udev                                           3093388          0                      3093388            0%         /dev
tmpfs                                          620764            8992                611772              2%         /run
/dev/sdb6                                   56126504        5536588          47715804          11%       /
tmpfs                                          3103808         156                   3103652            1%         /dev/shm
tmpfs                                          5120               4                       5116                  1%         /run/lock
tmpfs                                          3103808         0                       3103808            0%         /sys/fs/cgroup
/dev/sda1                                   961301832     154252696       758194712        17%       /home
cgmfs                                        100                  0                       100                    0%         /run/cgmanager/fs
192.168.1.150:/Servers             2882740800   1411161920     1471054592      49%       /media/NAS
tmpfs                                         620764            48                    620716               1%         /run/user/1000
```

```
jim@jim-X8ST3:~$ df -i
Filesystem                                  Inodes            IUsed               IFree                  IUse%    Mounted on
udev                                          204357            553                  203804               1%          /dev
tmpfs                                         209567            714                  208853               1%          /run
/dev/sdb6                                  3572912          228159            3344753             7%          /
tmpfs                                         209567            205                  209362               1%          /dev/shm
tmpfs                                         209567            6                      209561               1%          /run/lock
tmpfs                                         209567            17                    209550               1%          /sys/fs/cgroup
/dev/sda1                                  61054976        219565            60835411           1%          /home
cgmfs                                        209567            13                    209554               1%          /run/cgmanager/fs
192.168.1.150:/Servers            183050240      239437            182810803         1%          /media/NAS
tmpfs                                         209567            29                    209538               1%          /run/user/1000
```

Thanks for all the help on this, especially the links. I do always search for answers before asking, however, until I remembered that Steam was 32 bit and I had done a new install of 64 bit Ubuntu, the question I was asking was the wrong one, I had changed the hardware and partitioning and I too suspected that it was environment variables or something similar on restore, which was my original search and line of query.

Having said that the 32 bit version is still showing the "short of disk space error" which I don't appear to be. I have only set up myself as admin and my son's user and only restored his home directory. Until I get this bit running properly then I should not be taxing the system and I will be bringing bringing each user back on to this system one by one so everything is tested before I move on. We use a number of different systems in the house and I completely agree that Ubuntu LTS versions are the best for our working machines. The two machines where this is not the case are my son's bedroom computer which runs Lubuntu as it is an older less powerful machine and this one which is my "fun machine" with the newest graphics card, biggest screen etc. My home network is built around a central NAS so we can all share public and private areas on NAS, backup happens automatically and regularly, music, video and photos can be stored once and shared.

Jim

---

### Post by TheFu on 2015-09-22
Please run the commands again and copy/paste so everything lines up. Don't know why it doesn't.
```
$ df -h
Filesystem                       Size  Used Avail Use% Mounted on
/dev/mapper/istar--vg-root        52G   34G   15G  70% /
/dev/sdc2                        237M  127M   98M  57% /boot
/dev/mapper/istar--stuff-lv--tv  148G   60M  140G   1% /TV
/dev/mapper/istar--vg-lv_media   3.5T  3.0T  376G  89% /D
/dev/sdb1                        1.8T  1.7T   47G  98% /misc/2TB
romulus:/raid/media              1.8T  1.7T   31G  99% /R
romulus:/Data/r2                 1.3T  1.2T   16G  99% /S
/dev/sde1                        1.8T  1.5T  281G  84% /misc/b-2T
/dev/sdd2                        3.6T  3.6T     0 100% /misc/b-3.5T
```
See how this all lines up? I didn't touch anything.

Everything appears to be empty - so perhaps the startup error is a permissions thing (can't write) and being shown as "out of disk"?

---

### Post by uaebuntu on 2015-09-27
OK so we are making progress on many fonts. Having put the Forums editor into "advanced" mode I now have access to the CODE tag, and hopefully my columns will line up with out me having to try and manually format them

```

rmassey@jim-X8ST3:~$ df -h
Filesystem              Size  Used Avail Use% Mounted on
udev                    3.0G     0  3.0G   0% /dev
tmpfs                   607M  8.8M  598M   2% /run
/dev/sdb6                54G  5.3G   46G  11% /
tmpfs                   3.0G 1004K  3.0G   1% /dev/shm
tmpfs                   5.0M  4.0K  5.0M   1% /run/lock
tmpfs                   3.0G     0  3.0G   0% /sys/fs/cgroup
/dev/sda1               917G  144G  727G  17% /home
cgmfs                   100K     0  100K   0% /run/cgmanager/fs
192.168.1.150:/Servers  2.7T  1.4T  1.4T  50% /media/NAS
tmpfs                   607M   52K  607M   1% /run/user/1001

```

now running steam from a terminal as the admin gets it running OK in my user but I still get the "Are you running low on disk space error plus we can see the unpack error "Unpack runtime failed, error code 2"

```

rmassey@jim-X8ST3:~$ steam
Running Steam on ubuntu 15.04 32-bit
STEAM_RUNTIME is enabled automatically
Unpack runtime failed, error code 2
Error: Couldn't set up the Steam Runtime. Are you running low on disk space?
Continuing...
[2015-09-27 19:01:27] Startup - updater built Aug 19 2015 11:27:40
[2015-09-27 19:01:27] Verifying installation...
[2015-09-27 19:01:27] Verification complete
[2015-09-27 19:01:28] Shutdown

```

so checking this error it suggested running steam --reset 

```

rmassey@jim-X8ST3:~$ steam --reset
Error: Couldn't find bootstrap, it's not safe to reset Steam. Please contact technical support

```.

but it runs just fine (my son tested it) from my user so I doubt drivers on the nVidia card are the problem. I've checked a lot of other posts in this and different forum but as yet have not found one that makes sense to me or works when tried.

Jim

---

### Post by TheFu on 2015-09-27
Thanks for the code tags. You can enter those manually, BTW.

Running GUI programs with sudo is an issue and often screws with file permissions for files you don't want to be touched.
[https://askubuntu.com/questions/590072/steam-installation-error-in-ubuntu-14-04-lts](https://askubuntu.com/questions/590072/steam-installation-error-in-ubuntu-14-04-lts) - which it seems you've seen already.  

Can you confirm that steam was installed from the repos?

Have you looked at the log files in /var/log/?  Anything in there?  Can debug logging be enabled by steam? [https://developer.valvesoftware.com/wiki/Command_Line_Options](https://developer.valvesoftware.com/wiki/Command_Line_Options) has some other command line options.

---

