---
title: "How do you clean up synaptic package manager in 14.04?"
date: 2014-08-07
forum: General Help
---

### Post by UncleMonty on 2014-08-07
I get the following error message:

Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available, an older version of the failed index will be used. Otherwise, the repository will be ignored. Check your network connection and ensure the repository address is correct in 'Repositories' under 'Settings'.


Failed to fetch http://deb.torproject.org/torproject.org/dists/<DISTRIBUTION>/main/binary-i386/Packages  404  Not Found [IP: 154.35.132.70 80]
Failed to fetch http://deb.torproject.org/torproject.org/dists/<Tahr>/main/binary-i386/Packages  404  Not Found [IP: 154.35.132.70 80]
Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Bashing-om on 2014-08-07
UncleMonty; Hi !

Not sure yet what is going on with the "http://deb.torproject.org/torproject.org/dists/" repos.
Will have to look at your source.list files and make a determinataion.

This one:
[http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/trusty/main/binary-i386/Packages)
trusty is not yet available, disable this repository until the trusty release is supported.

Post back the outputs - between code tags - of terminal commands:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

We can then see what there is to find.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by UncleMonty on 2014-08-09
steve@house:~$ cat -n /etc/apt/sources.list
     1	# deb cdrom:[Ubuntu 14.04 LTS _Trusty Tahr_ - Release i386 (20140417)]/ trusty main restricted
     2	
     3	# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4	# newer versions of the distribution.
     5	deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty main restricted
     6	deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    11	deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty universe
    17	deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty universe
    18	deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates universe
    19	deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty multiverse
    27	deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty multiverse
    28	deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    29	deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
    37	deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
    38	
    39	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
    40	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
    41	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
    42	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
    43	deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
    44	deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
    45	
    46	## Uncomment the following two lines to add software from Canonical's
    47	## 'partner' repository.
    48	## This software is not part of Ubuntu, but is offered by Canonical and the
    49	## respective vendors as a service to Ubuntu users.
    50	# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    51	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
    52	
    53	## This software is not part of Ubuntu, but is offered by third-party
    54	## developers who want to ship their latest software.
    55	deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    56	deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
    57	deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <DISTRIBUTION> main
    58	# deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <DISTRIBUTION> main
    59	deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <Tahr> main
    60	# deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <Tahr> main
steve@house:~$ tail -v -n +1 /etc/apt/sources.list.d/*

---

### Post by UncleMonty on 2014-08-09
==> /etc/apt/sources.list.d/ehoover-compholio-trusty.list <==
deb [http://ppa.launchpad.net/ehoover/compholio/ubuntu](http://ppa.launchpad.net/ehoover/compholio/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/ehoover/compholio/ubuntu](http://ppa.launchpad.net/ehoover/compholio/ubuntu) trusty main

==> /etc/apt/sources.list.d/ehoover-compholio-trusty.list.save <==
deb [http://ppa.launchpad.net/ehoover/compholio/ubuntu](http://ppa.launchpad.net/ehoover/compholio/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/ehoover/compholio/ubuntu](http://ppa.launchpad.net/ehoover/compholio/ubuntu) trusty main

==> /etc/apt/sources.list.d/ffmulticonverter-stable-trusty.list <==
deb [http://ppa.launchpad.net/ffmulticonverter/stable/ubuntu](http://ppa.launchpad.net/ffmulticonverter/stable/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/ffmulticonverter/stable/ubuntu](http://ppa.launchpad.net/ffmulticonverter/stable/ubuntu) trusty main

==> /etc/apt/sources.list.d/ffmulticonverter-stable-trusty.list.save <==
deb [http://ppa.launchpad.net/ffmulticonverter/stable/ubuntu](http://ppa.launchpad.net/ffmulticonverter/stable/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/ffmulticonverter/stable/ubuntu](http://ppa.launchpad.net/ffmulticonverter/stable/ubuntu) trusty main

==> /etc/apt/sources.list.d/format-junkie-team-release-trusty.list <==
deb [http://ppa.launchpad.net/format-junkie-team/release/ubuntu](http://ppa.launchpad.net/format-junkie-team/release/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/format-junkie-team/release/ubuntu](http://ppa.launchpad.net/format-junkie-team/release/ubuntu) trusty main

==> /etc/apt/sources.list.d/format-junkie-team-release-trusty.list.save <==
deb [http://ppa.launchpad.net/format-junkie-team/release/ubuntu](http://ppa.launchpad.net/format-junkie-team/release/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/format-junkie-team/release/ubuntu](http://ppa.launchpad.net/format-junkie-team/release/ubuntu) trusty main

==> /etc/apt/sources.list.d/pipelight-stable-trusty.list <==
deb [http://ppa.launchpad.net/pipelight/stable/ubuntu](http://ppa.launchpad.net/pipelight/stable/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/pipelight/stable/ubuntu](http://ppa.launchpad.net/pipelight/stable/ubuntu) trusty main

==> /etc/apt/sources.list.d/pipelight-stable-trusty.list.save <==
deb [http://ppa.launchpad.net/pipelight/stable/ubuntu](http://ppa.launchpad.net/pipelight/stable/ubuntu) trusty main
# deb-src [http://ppa.launchpad.net/pipelight/stable/ubuntu](http://ppa.launchpad.net/pipelight/stable/ubuntu) trusty main

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_dmmedia_ubuntu.list <==
deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/dmmedia/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/dmmedia/ubuntu) trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_dmmedia_ubuntu.list.save <==
deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/dmmedia/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/dmmedia/ubuntu) trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_linux-disk-cleaner_ubuntu.list <==
deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/linux-disk-cleaner/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/linux-disk-cleaner/ubuntu) trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_outreel_ubuntu.list <==
deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/outreel/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/outreel/ubuntu) trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf

==> /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_outreel_ubuntu.list.save <==
deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/outreel/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/outreel/ubuntu) trusty main #Added by software-center; credentials stored in /etc/apt/auth.conf

==> /etc/apt/sources.list.d/stebbins-handbrake-releases-trusty.list <==

==> /etc/apt/sources.list.d/stebbins-handbrake-releases-trusty.list.save <==

---

### Post by grahammechanical on 2014-08-09
Remove the PPAs and then run the update/upgrade commands again. In 14.04 it is System Settings>Software and Updates>Other Software tab.

---

### Post by Bashing-om on 2014-08-09
UncleMonty; Welp;

Here is another piece of the puzzle to put into place.
These index's are in a non-valid format:
> 
57	deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <DISTRIBUTION> main
58	# deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <DISTRIBUTION> main
59	deb [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <Tahr> main
60	# deb-src [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <Tahr> main
 from "/etc/apt/sources.list" .
Comment them out too for the time being; and when the package management system runs clean, you (we) can investigate the proper formatting for the calls.
{maybe something akin to this " deb http://deb.torproject.org/torproject.org/trusty/main} - a quick check "looks" reasonable -

Once we are done paring down and like I say, the package manager in a consistent state, we can add back in " carefully " the indexes that you want to add back ( provided the packages are supported in the tusty release !).


So make the edits in "/etc/apt/sources.list", and run once more:
```

sudo apt-get update
sudo apt-get upgrade

```
and let's see where we now stand.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by UncleMonty on 2014-08-09
How do I access /etc/apt/sources.list? I tried sudo /etc/apt/sources.list - and got 'command does not exist'.

---

### Post by Bashing-om on 2014-08-09
UncleMonty; My apologies ;

I had "assumed" as there were modifications to the file, you had the knowledge/experience.
Do:
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-09aug2014
gksu gedit /etc/apt/sources.list

``` Which makes a backup of the current file, just in case of whatever perchances, then opens the file with administrative authority.
Once the file is opened in the text editor 'gedit', scroll down to the subject lines and place a comment (#) character at the start of the lines.
Save the file and exit back to terminal.

Now run:
```

sudo apt-get update
sudo apt-get upgrade

```
And let's see where things stand.

[INDENT][INDENT]it is all in the process of learning
[/INDENT][/INDENT]

---

### Post by Laurence_Montrose on 2014-08-11
I'm following this thread with interest because I'm having a similar problem.

I'm returning to Linux after a long time away, so I'm a little rusty,  but slowly remembering; and I've got 14.04 on a brand new System76  Bonobo.

Using Ubuntu Software Center - I loaded Synaptic, so I  could add some utility packages for R and Octave. I couldn't get  packages to download, so I tried to Reload packages, and I found that  every repository connection attempt was failing "failed to fetch". It  seems to be a complete failure in that there are no repository indexes  that appear to download. 

There were no software updates, and  since they had been running before, I unloaded Synaptic, and succeeded  in getting basic software upgrades working again. 

I tried  loading Synaptic again, and now I not only can't get updates through  Synaptic, the basic ones from System Settings - Software and updates  seem to have failed. - I tried to change the server, first from "Main"  to "Server for US", and when that didn't work, I tried to search for the  best available server, at which point I got a message that said no  suitable server could be identified, and it suggested I check the  network connection. 

sudo apt-get update and upgrade appear to work from a terminal in that the commands process and I don't see any error messages, but I haven't read all the man pages yet so there could be something subtle I'm not seeing.

---

### Post by Bashing-om on 2014-08-11
Laurence_Montrose; Hi ! Welcome .

OK, let's get the basics out of the way, clearing the desk for action.
Post back the complete output- between code tags -  of terminal commands:
```

cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

```
Now, let's "assume" there is no fault with the source index files and proceed to the next step, we need to KNOW . Again post the complete outputs:
```

sudo apt-get update
sdo apt-get upgade

```

OK, now IF these run clean, let's see what the package manager thinks for it's overall status:
```

sudo apt-get -f install
sudo dpkg -C
sudo dpkg --audit

```

we are now ready to get specific.

[INDENT][INDENT][INDENT]so a tale is told
[/INDENT][/INDENT][/INDENT]

---

### Post by UncleMonty on 2014-08-12
Fixed. Thanks everyone :):guitar:

---

### Post by Laurence_Montrose on 2014-08-12
Well that was interesting. First - it took me a while because I couldn't help going back and reading the man pages. (trying to remember what I used to know)

I ran the first two commands; everything was clean. Then I ran the update and upgrade commands, and lo and behold, all of a sudden I got the automatic system message I haven't seen for a while, saying there were a batch of updates to be installed. I installed them. I tried the update command the other day, so maybe the upgrade resolved the current problem.

I redirected the terminal into a series of files. 

I'm on my third attempt to upload the files.[ATTACH]255430[/ATTACH][ATTACH]255431[/ATTACH][ATTACH]255432[/ATTACH]

I can get the first three, but the fourth file is too large. I'm going to see if I can find some info lines to delete and see if I can upload it again, in a separate message  [ATTACH]255433[/ATTACH]

This is the point at which I tried to use synaptic to get some of the other R/Octave packages I wanted to investigate, and that's where I originally lost the update capability. Something in what you had me do unblocked the automated system updater, which is great. 

I'm not sure whether my best course of action would be to test synaptic again, or continue with the last couple of commands you recommended. I'm leaning toward the latter just because, but I'm running out of time tonite and I don't want to start too late to finish.

Regardless of the next step, thanks for your help on solving this initial problem (and maybe both problems?)

---

### Post by Bashing-om on 2014-08-13
Laurence_Montrose; Hey :

Slow down, relax. You are making this much more difficult than it ain't !
All ya got to do is run the commands, and copy and paste the results back to the post - between code tags !
see:
 code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

So, to this time your source.list files are good as is.
We do not know about the results of the update/upgrade process please include the complete output - between code tags to this post.
Take up there form my former response, and post ALL the results back to the posting.

[INDENT][INDENT]where there are solutions
[INDENT][INDENT][INDENT][INDENT]there are no problems
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Laurence_Montrose on 2014-08-14
Sorry, I must not have been clear. 

All four of the files were posted for the first four commands you suggested. I put the stdout into files I attached. When I attached them, the names of the separate files were run together with no spaces, but there are three in the first group, including the get1.txt file which contains the apt-get update results. In the next line, the get2.txt contains the results of the upgrade.

 The update and upgrade commands were successful, and immediately resulted in the system utility (Software Updater in the System Settings GUI) asking for permission to install the files. Click on the text files and you can see the results.

And today when I logged in, there were some additional updates, so whatever was temporarily wrong with the automated function has been fixed. Since I'm paranoid about updates after working in computer security, that's a huge load off my mind. I can get software that's visible through the Ubuntu Software Center, which includes only the baseline package for R.

Now I still have the problem that I can't get packages via Synaptic. In an optimistic frame of mind after seeing the first part go so well, I re-installed Synaptic and tried to mark and install a simple document. Marking OK; installing, no dice. I can see the Bayesian statistics package in Synaptic that I can't see in Ubuntu Software Center, so I'm still motivated to figure out what the logjam is.

---

### Post by Laurence_Montrose on 2014-08-14
[COLOR=#006400]So, with a little more time to finish all the commands in sequence, and using your suggested method instead of attaching a file, here's what I get today.[/COLOR]

```

merlinus@PerkySquirrel:~$ sudo apt-get update
[sudo] password for merlinus: 
Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://ppa.launchpad.net trusty InRelease                       
Ign http://archive.canonical.com trusty InRelease                    
Ign http://extras.ubuntu.com trusty InRelease                        
Ign http://us.archive.ubuntu.com trusty-updates InRelease            
Hit http://ppa.launchpad.net trusty Release.gpg
Ign http://us.archive.ubuntu.com trusty-backports InRelease          
Hit http://extras.ubuntu.com trusty Release.gpg                      
Ign http://archive.canonical.com trusty InRelease                    
Hit http://ppa.launchpad.net trusty Release                          
Ign http://us.archive.ubuntu.com trusty-security InRelease           
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://archive.canonical.com trusty Release.gpg                  
Hit http://ppa.launchpad.net trusty/main Sources                     
Hit http://extras.ubuntu.com trusty/main Sources                     
Get:1 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://archive.canonical.com trusty Release.gpg                  
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg        
Hit http://extras.ubuntu.com trusty/main amd64 Packages              
Get:2 http://us.archive.ubuntu.com trusty-security Release.gpg [933 B]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://archive.canonical.com trusty Release                      
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://archive.canonical.com trusty Release                                
Get:3 http://us.archive.ubuntu.com trusty-updates Release [59.7 kB]            
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://us.archive.ubuntu.com trusty-backports Release                      
Get:4 http://us.archive.ubuntu.com trusty-security Release [59.7 kB]           
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/multiverse Sources            
Hit http://archive.canonical.com trusty/partner Sources               
Hit http://us.archive.ubuntu.com trusty/main Sources                  
Ign http://ppa.launchpad.net trusty/main Translation-en_US            
Ign http://extras.ubuntu.com trusty/main Translation-en_US            
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages     
Ign http://ppa.launchpad.net trusty/main Translation-en               
Hit http://archive.canonical.com trusty/partner amd64 Packages        
Ign http://extras.ubuntu.com trusty/main Translation-en               
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://archive.canonical.com trusty/partner i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Get:5 http://us.archive.ubuntu.com trusty-updates/universe Sources [74.9 kB]
Get:6 http://us.archive.ubuntu.com trusty-updates/restricted Sources [1,408 B]
Get:7 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [3,230 B]
Get:8 http://us.archive.ubuntu.com trusty-updates/main Sources [108 kB]
Get:9 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [5,820 B]
Get:10 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [293 kB]
Ign http://archive.canonical.com trusty/partner Translation-en_US
Ign http://archive.canonical.com trusty/partner Translation-en                 
Ign http://archive.canonical.com trusty/partner Translation-en_US              
Get:11 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [181 kB]
Ign http://archive.canonical.com trusty/partner Translation-en                 
Get:12 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [8,221 B]
Get:13 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [5,820 B]
Get:14 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [289 kB] 
Get:15 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [182 kB]
Get:16 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [8,437 B]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Get:17 http://us.archive.ubuntu.com trusty-security/universe Sources [11.3 kB] 
Get:18 http://us.archive.ubuntu.com trusty-security/restricted Sources [14 B]  
Get:19 http://us.archive.ubuntu.com trusty-security/multiverse Sources [699 B] 
Get:20 http://us.archive.ubuntu.com trusty-security/main Sources [39.6 kB]     
Get:21 http://us.archive.ubuntu.com trusty-security/restricted amd64 Packages [14 B]
Get:22 http://us.archive.ubuntu.com trusty-security/main amd64 Packages [129 kB]
Get:23 http://us.archive.ubuntu.com trusty-security/universe amd64 Packages [46.2 kB]
Get:24 http://us.archive.ubuntu.com trusty-security/multiverse amd64 Packages [1,154 B]
Get:25 http://us.archive.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Get:26 http://us.archive.ubuntu.com trusty-security/main i386 Packages [125 kB]
Get:27 http://us.archive.ubuntu.com trusty-security/universe i386 Packages [46.1 kB]
Get:28 http://us.archive.ubuntu.com trusty-security/multiverse i386 Packages [1,398 B]
Hit http://us.archive.ubuntu.com trusty-security/main Translation-en           
Hit http://us.archive.ubuntu.com trusty-security/multiverse Translation-en     
Hit http://us.archive.ubuntu.com trusty-security/restricted Translation-en     
Hit http://us.archive.ubuntu.com trusty-security/universe Translation-en       
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 1,683 kB in 14s (114 kB/s)                                             
Reading package lists... Done

merlinus@PerkySquirrel:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
The following packages will be upgraded:
  libkscreen1 libpam-systemd libsystemd-daemon0 libsystemd-journal0
  libsystemd-login0 libudev1 libudev1:i386 net-tools systemd-services udev
10 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,359 kB of archives.
After this operation, 70.7 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main udev amd64 204-5ubuntu20.4 [735 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libudev1 i386 204-5ubuntu20.4 [34.2 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libudev1 amd64 204-5ubuntu20.4 [33.2 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libpam-systemd amd64 204-5ubuntu20.4 [25.5 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main systemd-services amd64 204-5ubuntu20.4 [197 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libsystemd-daemon0 amd64 204-5ubuntu20.4 [9,720 B]
Get:7 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libsystemd-login0 amd64 204-5ubuntu20.4 [26.7 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libsystemd-journal0 amd64 204-5ubuntu20.4 [49.6 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main net-tools amd64 1.60-25ubuntu2.1 [175 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe libkscreen1 amd64 1.0.5-0ubuntu1~ubuntu14.04 [73.3 kB]
Fetched 1,359 kB in 3s (357 kB/s)      
(Reading database ... 427438 files and directories currently installed.)
Preparing to unpack .../udev_204-5ubuntu20.4_amd64.deb ...
Adding 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
Unpacking udev (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../libudev1_204-5ubuntu20.4_i386.deb ...
De-configuring libudev1:amd64 (204-5ubuntu20.3) ...
Unpacking libudev1:i386 (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../libudev1_204-5ubuntu20.4_amd64.deb ...
Unpacking libudev1:amd64 (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../libpam-systemd_204-5ubuntu20.4_amd64.deb ...
systemd-logind stop/waiting
Unpacking libpam-systemd:amd64 (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../systemd-services_204-5ubuntu20.4_amd64.deb ...
Unpacking systemd-services (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../libsystemd-daemon0_204-5ubuntu20.4_amd64.deb ...
Unpacking libsystemd-daemon0:amd64 (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../libsystemd-login0_204-5ubuntu20.4_amd64.deb ...
Unpacking libsystemd-login0:amd64 (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../libsystemd-journal0_204-5ubuntu20.4_amd64.deb ...
Unpacking libsystemd-journal0:amd64 (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../net-tools_1.60-25ubuntu2.1_amd64.deb ...
Unpacking net-tools (1.60-25ubuntu2.1) over (1.60-25ubuntu2) ...
Preparing to unpack .../libkscreen1_1.0.5-0ubuntu1~ubuntu14.04_amd64.deb ...
Unpacking libkscreen1 (1.0.5-0ubuntu1~ubuntu14.04) over (1.0.2-0ubuntu2) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.6.7.1-1) ...
Setting up libudev1:amd64 (204-5ubuntu20.4) ...
Setting up libudev1:i386 (204-5ubuntu20.4) ...
Setting up udev (204-5ubuntu20.4) ...
udev stop/waiting
udev start/running, process 4638
Removing 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
update-initramfs: deferring update (trigger activated)
Setting up libsystemd-daemon0:amd64 (204-5ubuntu20.4) ...
Setting up systemd-services (204-5ubuntu20.4) ...
Setting up libpam-systemd:amd64 (204-5ubuntu20.4) ...
systemd-logind start/running, process 4706
Setting up libsystemd-login0:amd64 (204-5ubuntu20.4) ...
Setting up libsystemd-journal0:amd64 (204-5ubuntu20.4) ...
Setting up net-tools (1.60-25ubuntu2.1) ...
Setting up libkscreen1 (1.0.5-0ubuntu1~ubuntu14.04) ...
Processing triggers for libc-bin (2.19-0ubuntu6.1) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-34-generic

merlinus@PerkySquirrel:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

no results from either of the last two commands, just a return to the prompt.

```
[COLOR=#006400]
Just out of curiosity, can you explain the difference between dpkg -C and dpkg --audit? From the man page, it looks like they're the same thing, and since I got a null response from both, I can't compare. When I learned UNIX originally, it was for doing system-level integration and test (IV&V), so I'm relatively weak in this area. (I'm taking notes on this stuff you're teaching me already.)[/COLOR]

---

### Post by Bashing-om on 2014-08-14
Laurence_Montrose; OK,

Try and isolate the fault to synaptic.
From the command line using the back end of the package management system "apt-cache" :
What does apt-cache see:
```

apt-cache show r-cran-bayesm

```
Is that the package you want ?

What results when installing it from terminal ?
```

sudo apt-get install r-cran-bayesm

```
No problem ?  Remove it and see what synaptic does.
```

sudo apt-get purge r-cran-bayesm

```
Is synaptic able to install the package ?

[INDENT][INDENT]fault isolation
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-08-14
Laurence_Montrose; OK,

Try and isolate the fault to synaptic.
From the command line using the back end of the package management system "apt-cache" :
What does apt-cache see:
```

apt-cache show r-cran-bayesm

```
Is that the package you want ?

What results when installing it from terminal ?
```

sudo apt-get install r-cran-bayesm

```
No problem ?  Remove it and see what synaptic does.
```

sudo apt-get purge r-cran-bayesm

```
Is synaptic able to install the package ?

[INDENT][INDENT]fault isolation
[/INDENT][/INDENT]

---

### Post by Laurence_Montrose on 2014-08-14
[COLOR=#006400]So, with a little more time to finish all the commands in sequence, and using your suggested method instead of attaching a file, here's what I get today.[/COLOR]

```

merlinus@PerkySquirrel:~$ sudo apt-get update
[sudo] password for merlinus: 
Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://ppa.launchpad.net trusty InRelease                       
Ign http://archive.canonical.com trusty InRelease                    
Ign http://extras.ubuntu.com trusty InRelease                        
Ign http://us.archive.ubuntu.com trusty-updates InRelease            
Hit http://ppa.launchpad.net trusty Release.gpg
Ign http://us.archive.ubuntu.com trusty-backports InRelease          
Hit http://extras.ubuntu.com trusty Release.gpg                      
Ign http://archive.canonical.com trusty InRelease                    
Hit http://ppa.launchpad.net trusty Release                          
Ign http://us.archive.ubuntu.com trusty-security InRelease           
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://archive.canonical.com trusty Release.gpg                  
Hit http://ppa.launchpad.net trusty/main Sources                     
Hit http://extras.ubuntu.com trusty/main Sources                     
Get:1 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://archive.canonical.com trusty Release.gpg                  
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg        
Hit http://extras.ubuntu.com trusty/main amd64 Packages              
Get:2 http://us.archive.ubuntu.com trusty-security Release.gpg [933 B]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://archive.canonical.com trusty Release                      
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://archive.canonical.com trusty Release                                
Get:3 http://us.archive.ubuntu.com trusty-updates Release [59.7 kB]            
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://us.archive.ubuntu.com trusty-backports Release                      
Get:4 http://us.archive.ubuntu.com trusty-security Release [59.7 kB]           
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/multiverse Sources            
Hit http://archive.canonical.com trusty/partner Sources               
Hit http://us.archive.ubuntu.com trusty/main Sources                  
Ign http://ppa.launchpad.net trusty/main Translation-en_US            
Ign http://extras.ubuntu.com trusty/main Translation-en_US            
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages     
Ign http://ppa.launchpad.net trusty/main Translation-en               
Hit http://archive.canonical.com trusty/partner amd64 Packages        
Ign http://extras.ubuntu.com trusty/main Translation-en               
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://archive.canonical.com trusty/partner i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Get:5 http://us.archive.ubuntu.com trusty-updates/universe Sources [74.9 kB]
Get:6 http://us.archive.ubuntu.com trusty-updates/restricted Sources [1,408 B]
Get:7 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [3,230 B]
Get:8 http://us.archive.ubuntu.com trusty-updates/main Sources [108 kB]
Get:9 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [5,820 B]
Get:10 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [293 kB]
Ign http://archive.canonical.com trusty/partner Translation-en_US
Ign http://archive.canonical.com trusty/partner Translation-en                 
Ign http://archive.canonical.com trusty/partner Translation-en_US              
Get:11 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [181 kB]
Ign http://archive.canonical.com trusty/partner Translation-en                 
Get:12 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [8,221 B]
Get:13 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [5,820 B]
Get:14 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [289 kB] 
Get:15 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [182 kB]
Get:16 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [8,437 B]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Get:17 http://us.archive.ubuntu.com trusty-security/universe Sources [11.3 kB] 
Get:18 http://us.archive.ubuntu.com trusty-security/restricted Sources [14 B]  
Get:19 http://us.archive.ubuntu.com trusty-security/multiverse Sources [699 B] 
Get:20 http://us.archive.ubuntu.com trusty-security/main Sources [39.6 kB]     
Get:21 http://us.archive.ubuntu.com trusty-security/restricted amd64 Packages [14 B]
Get:22 http://us.archive.ubuntu.com trusty-security/main amd64 Packages [129 kB]
Get:23 http://us.archive.ubuntu.com trusty-security/universe amd64 Packages [46.2 kB]
Get:24 http://us.archive.ubuntu.com trusty-security/multiverse amd64 Packages [1,154 B]
Get:25 http://us.archive.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Get:26 http://us.archive.ubuntu.com trusty-security/main i386 Packages [125 kB]
Get:27 http://us.archive.ubuntu.com trusty-security/universe i386 Packages [46.1 kB]
Get:28 http://us.archive.ubuntu.com trusty-security/multiverse i386 Packages [1,398 B]
Hit http://us.archive.ubuntu.com trusty-security/main Translation-en           
Hit http://us.archive.ubuntu.com trusty-security/multiverse Translation-en     
Hit http://us.archive.ubuntu.com trusty-security/restricted Translation-en     
Hit http://us.archive.ubuntu.com trusty-security/universe Translation-en       
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 1,683 kB in 14s (114 kB/s)                                             
Reading package lists... Done

merlinus@PerkySquirrel:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
The following packages will be upgraded:
  libkscreen1 libpam-systemd libsystemd-daemon0 libsystemd-journal0
  libsystemd-login0 libudev1 libudev1:i386 net-tools systemd-services udev
10 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,359 kB of archives.
After this operation, 70.7 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main udev amd64 204-5ubuntu20.4 [735 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libudev1 i386 204-5ubuntu20.4 [34.2 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libudev1 amd64 204-5ubuntu20.4 [33.2 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libpam-systemd amd64 204-5ubuntu20.4 [25.5 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main systemd-services amd64 204-5ubuntu20.4 [197 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libsystemd-daemon0 amd64 204-5ubuntu20.4 [9,720 B]
Get:7 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libsystemd-login0 amd64 204-5ubuntu20.4 [26.7 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libsystemd-journal0 amd64 204-5ubuntu20.4 [49.6 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main net-tools amd64 1.60-25ubuntu2.1 [175 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe libkscreen1 amd64 1.0.5-0ubuntu1~ubuntu14.04 [73.3 kB]
Fetched 1,359 kB in 3s (357 kB/s)      
(Reading database ... 427438 files and directories currently installed.)
Preparing to unpack .../udev_204-5ubuntu20.4_amd64.deb ...
Adding 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
Unpacking udev (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../libudev1_204-5ubuntu20.4_i386.deb ...
De-configuring libudev1:amd64 (204-5ubuntu20.3) ...
Unpacking libudev1:i386 (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../libudev1_204-5ubuntu20.4_amd64.deb ...
Unpacking libudev1:amd64 (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../libpam-systemd_204-5ubuntu20.4_amd64.deb ...
systemd-logind stop/waiting
Unpacking libpam-systemd:amd64 (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../systemd-services_204-5ubuntu20.4_amd64.deb ...
Unpacking systemd-services (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../libsystemd-daemon0_204-5ubuntu20.4_amd64.deb ...
Unpacking libsystemd-daemon0:amd64 (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../libsystemd-login0_204-5ubuntu20.4_amd64.deb ...
Unpacking libsystemd-login0:amd64 (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../libsystemd-journal0_204-5ubuntu20.4_amd64.deb ...
Unpacking libsystemd-journal0:amd64 (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../net-tools_1.60-25ubuntu2.1_amd64.deb ...
Unpacking net-tools (1.60-25ubuntu2.1) over (1.60-25ubuntu2) ...
Preparing to unpack .../libkscreen1_1.0.5-0ubuntu1~ubuntu14.04_amd64.deb ...
Unpacking libkscreen1 (1.0.5-0ubuntu1~ubuntu14.04) over (1.0.2-0ubuntu2) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.6.7.1-1) ...
Setting up libudev1:amd64 (204-5ubuntu20.4) ...
Setting up libudev1:i386 (204-5ubuntu20.4) ...
Setting up udev (204-5ubuntu20.4) ...
udev stop/waiting
udev start/running, process 4638
Removing 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
update-initramfs: deferring update (trigger activated)
Setting up libsystemd-daemon0:amd64 (204-5ubuntu20.4) ...
Setting up systemd-services (204-5ubuntu20.4) ...
Setting up libpam-systemd:amd64 (204-5ubuntu20.4) ...
systemd-logind start/running, process 4706
Setting up libsystemd-login0:amd64 (204-5ubuntu20.4) ...
Setting up libsystemd-journal0:amd64 (204-5ubuntu20.4) ...
Setting up net-tools (1.60-25ubuntu2.1) ...
Setting up libkscreen1 (1.0.5-0ubuntu1~ubuntu14.04) ...
Processing triggers for libc-bin (2.19-0ubuntu6.1) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-34-generic

merlinus@PerkySquirrel:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

no results from either of the last two commands, just a return to the prompt.

```
[COLOR=#006400]
Just out of curiosity, can you explain the difference between dpkg -C and dpkg --audit? From the man page, it looks like they're the same thing, and since I got a null response from both, I can't compare. When I learned UNIX originally, it was for doing system-level integration and test (IV&V), so I'm relatively weak in this area. (I'm taking notes on this stuff you're teaching me already.)[/COLOR]

---

### Post by Laurence_Montrose on 2014-08-14
[COLOR=#008000]So, with a little more time to finish all the commands in sequence, and using your suggested method instead of attaching a file, here's what I get today.[/COLOR]

```

merlinus@PerkySquirrel:~$ sudo apt-get update
[sudo] password for merlinus:
Ign http://us.archive.ubuntu.com trusty InRelease
Ign http://ppa.launchpad.net trusty InRelease                       
Ign http://archive.canonical.com trusty InRelease                    
Ign http://extras.ubuntu.com trusty InRelease                        
Ign http://us.archive.ubuntu.com trusty-updates InRelease            
Hit http://ppa.launchpad.net trusty Release.gpg
Ign http://us.archive.ubuntu.com trusty-backports InRelease          
Hit http://extras.ubuntu.com trusty Release.gpg                      
Ign http://archive.canonical.com trusty InRelease                    
Hit http://ppa.launchpad.net trusty Release                          
Ign http://us.archive.ubuntu.com trusty-security InRelease           
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://archive.canonical.com trusty Release.gpg                  
Hit http://ppa.launchpad.net trusty/main Sources                     
Hit http://extras.ubuntu.com trusty/main Sources                     
Get:1 http://us.archive.ubuntu.com trusty-updates Release.gpg [933 B]
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://archive.canonical.com trusty Release.gpg                  
Hit http://us.archive.ubuntu.com trusty-backports Release.gpg        
Hit http://extras.ubuntu.com trusty/main amd64 Packages              
Get:2 http://us.archive.ubuntu.com trusty-security Release.gpg [933 B]
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Hit http://archive.canonical.com trusty Release                      
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://archive.canonical.com trusty Release                                
Get:3 http://us.archive.ubuntu.com trusty-updates Release [59.7 kB]            
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://us.archive.ubuntu.com trusty-backports Release                      
Get:4 http://us.archive.ubuntu.com trusty-security Release [59.7 kB]           
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/multiverse Sources            
Hit http://archive.canonical.com trusty/partner Sources               
Hit http://us.archive.ubuntu.com trusty/main Sources                  
Ign http://ppa.launchpad.net trusty/main Translation-en_US            
Ign http://extras.ubuntu.com trusty/main Translation-en_US            
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages     
Ign http://ppa.launchpad.net trusty/main Translation-en               
Hit http://archive.canonical.com trusty/partner amd64 Packages        
Ign http://extras.ubuntu.com trusty/main Translation-en               
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages
Hit http://archive.canonical.com trusty/partner i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages
Hit http://us.archive.ubuntu.com trusty/main i386 Packages
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages
Hit http://us.archive.ubuntu.com trusty/main Translation-en
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en
Hit http://us.archive.ubuntu.com trusty/universe Translation-en
Get:5 http://us.archive.ubuntu.com trusty-updates/universe Sources [74.9 kB]
Get:6 http://us.archive.ubuntu.com trusty-updates/restricted Sources [1,408 B]
Get:7 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [3,230 B]
Get:8 http://us.archive.ubuntu.com trusty-updates/main Sources [108 kB]
Get:9 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [5,820 B]
Get:10 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [293 kB]
Ign http://archive.canonical.com trusty/partner Translation-en_US
Ign http://archive.canonical.com trusty/partner Translation-en                 
Ign http://archive.canonical.com trusty/partner Translation-en_US              
Get:11 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [181 kB]
Ign http://archive.canonical.com trusty/partner Translation-en                 
Get:12 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [8,221 B]
Get:13 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [5,820 B]
Get:14 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [289 kB]
Get:15 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [182 kB]
Get:16 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [8,437 B]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en            
Hit http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/restricted Translation-en      
Hit http://us.archive.ubuntu.com trusty-updates/universe Translation-en        
Hit http://us.archive.ubuntu.com trusty-backports/restricted Sources           
Hit http://us.archive.ubuntu.com trusty-backports/universe Sources             
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Sources           
Hit http://us.archive.ubuntu.com trusty-backports/main Sources                 
Hit http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages      
Hit http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com trusty-backports/main amd64 Packages          
Hit http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/universe i386 Packages       
Hit http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com trusty-backports/main i386 Packages           
Hit http://us.archive.ubuntu.com trusty-backports/main Translation-en          
Hit http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/restricted Translation-en    
Hit http://us.archive.ubuntu.com trusty-backports/universe Translation-en      
Get:17 http://us.archive.ubuntu.com trusty-security/universe Sources [11.3 kB]
Get:18 http://us.archive.ubuntu.com trusty-security/restricted Sources [14 B]  
Get:19 http://us.archive.ubuntu.com trusty-security/multiverse Sources [699 B]
Get:20 http://us.archive.ubuntu.com trusty-security/main Sources [39.6 kB]     
Get:21 http://us.archive.ubuntu.com trusty-security/restricted amd64 Packages [14 B]
Get:22 http://us.archive.ubuntu.com trusty-security/main amd64 Packages [129 kB]
Get:23 http://us.archive.ubuntu.com trusty-security/universe amd64 Packages [46.2 kB]
Get:24 http://us.archive.ubuntu.com trusty-security/multiverse amd64 Packages [1,154 B]
Get:25 http://us.archive.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Get:26 http://us.archive.ubuntu.com trusty-security/main i386 Packages [125 kB]
Get:27 http://us.archive.ubuntu.com trusty-security/universe i386 Packages [46.1 kB]
Get:28 http://us.archive.ubuntu.com trusty-security/multiverse i386 Packages [1,398 B]
Hit http://us.archive.ubuntu.com trusty-security/main Translation-en           
Hit http://us.archive.ubuntu.com trusty-security/multiverse Translation-en     
Hit http://us.archive.ubuntu.com trusty-security/restricted Translation-en     
Hit http://us.archive.ubuntu.com trusty-security/universe Translation-en       
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 1,683 kB in 14s (114 kB/s)                                             
Reading package lists... Done

merlinus@PerkySquirrel:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
The following packages will be upgraded:
  libkscreen1 libpam-systemd libsystemd-daemon0 libsystemd-journal0
  libsystemd-login0 libudev1 libudev1:i386 net-tools systemd-services udev
10 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,359 kB of archives.
After this operation, 70.7 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main udev amd64 204-5ubuntu20.4 [735 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libudev1 i386 204-5ubuntu20.4 [34.2 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libudev1 amd64 204-5ubuntu20.4 [33.2 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libpam-systemd amd64 204-5ubuntu20.4 [25.5 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main systemd-services amd64 204-5ubuntu20.4 [197 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libsystemd-daemon0 amd64 204-5ubuntu20.4 [9,720 B]
Get:7 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libsystemd-login0 amd64 204-5ubuntu20.4 [26.7 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libsystemd-journal0 amd64 204-5ubuntu20.4 [49.6 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main net-tools amd64 1.60-25ubuntu2.1 [175 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe libkscreen1 amd64 1.0.5-0ubuntu1~ubuntu14.04 [73.3 kB]
Fetched 1,359 kB in 3s (357 kB/s)      
(Reading database ... 427438 files and directories currently installed.)
Preparing to unpack .../udev_204-5ubuntu20.4_amd64.deb ...
Adding 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
Unpacking udev (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../libudev1_204-5ubuntu20.4_i386.deb ...
De-configuring libudev1:amd64 (204-5ubuntu20.3) ...
Unpacking libudev1:i386 (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../libudev1_204-5ubuntu20.4_amd64.deb ...
Unpacking libudev1:amd64 (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../libpam-systemd_204-5ubuntu20.4_amd64.deb ...
systemd-logind stop/waiting
Unpacking libpam-systemd:amd64 (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../systemd-services_204-5ubuntu20.4_amd64.deb ...
Unpacking systemd-services (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../libsystemd-daemon0_204-5ubuntu20.4_amd64.deb ...
Unpacking libsystemd-daemon0:amd64 (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../libsystemd-login0_204-5ubuntu20.4_amd64.deb ...
Unpacking libsystemd-login0:amd64 (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../libsystemd-journal0_204-5ubuntu20.4_amd64.deb ...
Unpacking libsystemd-journal0:amd64 (204-5ubuntu20.4) over (204-5ubuntu20.3) ...
Preparing to unpack .../net-tools_1.60-25ubuntu2.1_amd64.deb ...
Unpacking net-tools (1.60-25ubuntu2.1) over (1.60-25ubuntu2) ...
Preparing to unpack .../libkscreen1_1.0.5-0ubuntu1~ubuntu14.04_amd64.deb ...
Unpacking libkscreen1 (1.0.5-0ubuntu1~ubuntu14.04) over (1.0.2-0ubuntu2) ...
Processing triggers for ureadahead (0.100.0-16) ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db (2.6.7.1-1) ...
Setting up libudev1:amd64 (204-5ubuntu20.4) ...
Setting up libudev1:i386 (204-5ubuntu20.4) ...
Setting up udev (204-5ubuntu20.4) ...
udev stop/waiting
udev start/running, process 4638
Removing 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
update-initramfs: deferring update (trigger activated)
Setting up libsystemd-daemon0:amd64 (204-5ubuntu20.4) ...
Setting up systemd-services (204-5ubuntu20.4) ...
Setting up libpam-systemd:amd64 (204-5ubuntu20.4) ...
systemd-logind start/running, process 4706
Setting up libsystemd-login0:amd64 (204-5ubuntu20.4) ...
Setting up libsystemd-journal0:amd64 (204-5ubuntu20.4) ...
Setting up net-tools (1.60-25ubuntu2.1) ...
Setting up libkscreen1 (1.0.5-0ubuntu1~ubuntu14.04) ...
Processing triggers for libc-bin (2.19-0ubuntu6.1) ...
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-34-generic

merlinus@PerkySquirrel:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

no results from either of the last two commands, just a return to the prompt.

```

[COLOR=#008000]Just out of curiosity, can you explain the difference between dpkg -C and dpkg --audit? From the man page, it looks like they're the same thing, and since I got a null response from both, I can't compare. When I learned UNIX originally, it was for doing system-level integration and test (IV&V), so I'm relatively weak in this area. (I'm taking notes on this stuff you're teaching me already.)[/COLOR]

---

### Post by Laurence_Montrose on 2014-08-19
[COLOR=#008000]Next stage of debugging. [/COLOR]

```

Package: r-cran-bayesm
Priority: optional
Section: universe/math
Installed-Size: 2220
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Chris Lawrence <lawrencc@debian.org>
Architecture: amd64
Version: 2.2-5-1
Depends: r-base-core (>= 3.0.0-2ubuntu1), libc6 (>= 2.2.5), libstdc++6 (>= 4.1.1)
Filename: pool/universe/r/r-cran-bayesm/r-cran-bayesm_2.2-5-1_amd64.deb
Size: 2022636
MD5sum: 3939268086648fd18a6393a44cfd4618
SHA1: 73dcc385c8f2db6cb1a3ec3b2987ff4f4eee7323
SHA256: f85183072117584bfc55bd7d776fe92052c15bd7c61b6dc935a1cde5108e1c64
Description-en: GNU R package for Bayesian inference
 The bayesm package covers many important models used in marketing and
 micro-econometrics applications. The package includes:
 .
  * Bayes Regression (univariate or multivariate dep var)
  * Multinomial Logit (MNL) and Multinomial Probit (MNP)
  * Multivariate Probit,
  * Multivariate Mixtures of Normals
  * Hierarchical Linear Models with normal prior and covariates
  * Hierarchical Multinomial Logits with mixture of normals prior and
    covariates
  * Bayesian analysis of choice-based conjoint data
  * Bayesian treatment of linear instrumental variables models
  * Analyis of Multivariate Ordinal survey data with scale usage heterogeneity
    (as in Rossi et al, JASA (01)).
 .
 For further reference, consult the authors' book, _Bayesian Statistics and
 Marketing_ by Allenby, McCulloch and Rossi.
Description-md5: 6f649751db2fffd16683aa065ef0eeca
Homepage: http://www.perossi.org/home/bsm-1
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

merlinus@PerkySquirrel:~$ sudo apt-get install r-cran-bayesm
[sudo] password for merlinus: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
The following NEW packages will be installed:
  r-cran-bayesm
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,023 kB of archives.
After this operation, 2,273 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty/universe r-cran-bayesm amd64 2.2-5-1 [2,023 kB]
Fetched 2,023 kB in 4s (433 kB/s)          
Selecting previously unselected package r-cran-bayesm.
(Reading database ... 427438 files and directories currently installed.)
Preparing to unpack .../r-cran-bayesm_2.2-5-1_amd64.deb ...
Unpacking r-cran-bayesm (2.2-5-1) ...
Setting up r-cran-bayesm (2.2-5-1) ...

merlinus@PerkySquirrel:~$ sudo apt-get purge r-cran-bayesm
[sudo] password for merlinus: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  kde-l10n-engb
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED:
  r-cran-bayesm*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 2,273 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 427482 files and directories currently installed.)
Removing r-cran-bayesm (2.2-5-1) ...
```

[COLOR=#008000]OK - I opened Synaptic, and tried the first thing, which was looking for the package you found. It wasn't visible, so I thought maybe the package list might be stale, so I clicked on the reload icon. After nothing happened for a while, I canceled the status display, and got an error message saying that Synaptic "failed to fetch" any of the repositories. I marked another package, got a message back about a couple other package dependencies, marked them and then got the same message (not too surprising) of "failed to fetch". 

All the manual procedures you've suggested appear to be working correctly, but Synaptic can't see the repositories or gain access to them. 

I don't know if it's significant or not but I don't see a real time indication of the status in the status dialog box; it's only when I close the window that a second one pops up with the error messages. That's a change from the behavior I saw last week, before I removed the Synaptic application and reloaded it.

The dialog box Synaptic displays is the same one I see from the Ubuntu System Settings Updater, so the resources exist, they're visible to my system, but Synaptic can't negotiate them. Poking around, I found an old archived warning that Synaptic couldn't work over WiFi but that's the only info I've seen that would appear to be symptomatically related.[/COLOR]

[COLOR=#008000]I used this utility on an older system, and I really liked it. I haven't found anything that it doesn't appear able to do in terms of filtering, or displaying results by the different categories. If you look in the listing above, there's a reference to a file suggested for autoremoval. Out of curiosity, I did that, and it worked like a charm. It seems like the basic capability is there, except for the ability to reach out to the network and see repositories. [/COLOR]

---

### Post by Bashing-om on 2014-08-19
Laurence_Montrose; Hey;

I agree, real strange that the terminal package management has no problem, but synaptic does, and you have removed the application and re-installed.

I am done for this session - too many errors on my part - I will sleep on this, and give it my consideration in my Am.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-08-20
Laurence_Montrose; HUMMM...

Not making a lot of headway here in my thinking. 
As the problem is isolated to 'synaptic' alone and of it's self:
what returns:
```

apt-cache policy synaptic

```
depending on that, we see what results with 're-configuring' synaptic.

[INDENT][INDENT]tis a puzzle
[/INDENT][/INDENT]

---

### Post by Laurence_Montrose on 2014-09-08
Sorry to leave you hanging, but it was a nice vacation. 

```

synaptic:
  Installed: 0.81.1ubuntu1
  Candidate: 0.81.1ubuntu1
  Version table:
 *** 0.81.1ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     0.81.1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages

```

I don't know enough about the distribution archives, but the fact that there's only a single line item, where apt-get update gives me dozens, makes me wonder. I'm going to see if I can identify a package that looks like it's resident at the /ubuntu/ trusty-updates/universe amd64 location, and see if that works. That would tell me Synaptic doesn't use the full list.

---

### Post by Bashing-om on 2014-09-08
Laurence_Montrose; welp;

That is the correct version installed, and there is no alternate version available.
What does the package manager think ?
```

dpkg -l synaptic

```
that is a lower case "L"

If that comes back with 'ii' in the 1st column ->
```

sudo dpkg-reconfigure synaptic

```

let's see what that does.

[INDENT][INDENT]sometimes I wonder
[/INDENT][/INDENT]

---

### Post by Laurence_Montrose on 2014-09-08
Just out of curiosity after looking at the "failed to fetch .... connection failed" message from Synaptic, I tried turning off my firewall. No effect. 

Back to your suggestions. I did get the "ii" back  from dpkg, so I tried dpkg-reconfigure. There was no action and an immediate prompt in the terminal. That's what I would expect if there was no configuration action.

---

### Post by mcduck on 2014-09-09
Just to make sure, have you checked the network settings in Synaptic (Settings->Preferences->Network). Make sure it's set to direct Internet connection, not proxy.

---

### Post by Bashing-om on 2014-09-09
Laurence_Montrose; Sheesshh;

I am out of ideas ! .. I hate when that happens.
Looks like our mcduck has the avenue to pursue - Thanks for that !

Package manager is happy and sees no fault, so yeah .. gotta be in the configuration, somewhere.

[INDENT][INDENT]must be a reason
[/INDENT][/INDENT]

---

