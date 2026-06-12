---
title: "Unable to install Nvidia drivers - Unable to locate package"
date: 2017-08-29
forum: General Help
---

### Post by tbrady85 on 2017-08-29
So last night I decided to update my nvidia drivers to 381 following some steps I found online.  Here are the steps I followed:


```
    sudo apt-get purge nvidia*
    sudo add-apt-repository ppa:graphics-drivers/ppa
    sudo apt-get update
    sudo apt-get install nvidia-381

```

Whenever I get to "sudo apt-get install nvidia-381" command I receive "Unable to locate package nvidia-381"


I've searched everywhere and also posted on StackExchange but can't find a solution this. Any ideas?

Here's the stack exchange thread: [https://askubuntu.com/questions/951046/unable-to-install-nvidia-drivers-unable-to-locate-package?noredirect=1#comment1514884_951046](https://askubuntu.com/questions/951046/unable-to-install-nvidia-drivers-unable-to-locate-package?noredirect=1#comment1514884_951046) 


Here is my output:


```
    tyler@tyler-ubuntu:~$ sudo add-apt-repository ppa:graphics-drivers/ppa
     Fresh drivers from upstream, currently shipping Nvidia.
    
    ## Current Status
    
    Current official release: `nvidia-381` (381.22)
    Current long-lived branch release: `nvidia-375` (375.66)
    
    For G8x, G9x and GT2xx GPUs use `nvidia-340` (340.102)
    For NV4x and G7x GPUs use `nvidia-304` (304.135)
    
    Support timeframes for Unix legacy GPU releases:
    https://nvidia.custhelp.com/app/answers/detail/a_id/3142
    
    ## What we're working on right now:
    
    - Normal driver updates
    - Help Wanted: Mesa Updates for Intel/AMD users, ping us if you want to help do this work, we're shorthanded.
    
    ## WARNINGS:
    
    This PPA is currently in testing, you should be experienced with packaging before you dive in here:
    
    Volunteers welcome! See also: https://github.com/mamarley/nvidia-graphics-drivers/
    
    ### How you can help:
    
    ## Install PTS and benchmark your gear:
    
        sudo apt-get install phoronix-test-suite
    
    Run the benchmark:
    
        phoronix-test-suite default-benchmark openarena xonotic tesseract gputest unigine-valley
    
    and then say yes when it asks you to submit your results to openbechmarking.org. Then grab a cup of coffee, it takes a bit for the benchmarks to run. Depending on the version of Ubuntu you're using it might preferable for you to grabs PTS from upstream directly: http://www.phoronix-test-suite.com/?k=downloads
    
    ## Share your results with the community:
    
    Post a link to your results (or any other feedback to): https://launchpad.net/~graphics-drivers-testers
    
    Remember to rerun and resubmit the benchmarks after driver upgrades, this will allow us to gather a bunch of data on performance that we can share with everybody.
    
    If you run into old documentation referring to other PPAs, you can help us by consolidating references to this PPA.
    
    If someone wants to go ahead and start prototyping on `software-properties-gtk` on what the GUI should look like, please start hacking!
    
    ## Help us Help You!
    
    We use the donation funds to get the developers hardware to test and upload these drivers, please consider donating to the "community" slider on the donation page if you're loving this PPA:
    
    http://www.ubuntu.com/download/desktop/contribute
     More info: https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa
    Press [ENTER] to continue or ctrl-c to cancel adding it
    
    gpg: keybox '/tmp/tmpf35j9cfi/pubring.gpg' created
    gpg: /tmp/tmpf35j9cfi/trustdb.gpg: trustdb created
    gpg: key FCAE110B1118213C: public key "Launchpad PPA for Graphics Drivers Team" imported
    gpg: Total number processed: 1
    gpg:               imported: 1
    OK
    tyler@tyler-ubuntu:~$ sudo apt-get update
    Hit:1 http://repo.steampowered.com/steam precise InRelease
    Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease                   
    Hit:3 http://packages.microsoft.com/repos/vscode stable InRelease              
    Hit:4 http://us.archive.ubuntu.com/ubuntu zesty InRelease                      
    Hit:5 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu zesty InRelease     
    Hit:6 http://dl.google.com/linux/chrome/deb stable Release                     
    Get:7 http://security.ubuntu.com/ubuntu zesty-security InRelease [89.2 kB]     
    Hit:8 http://us.archive.ubuntu.com/ubuntu zesty-updates InRelease              
    Get:9 http://us.archive.ubuntu.com/ubuntu zesty-backports InRelease [89.2 kB]  
    Hit:10 http://ppa.launchpad.net/noobslab/macbuntu/ubuntu zesty InRelease       
    Hit:11 http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu zesty InRelease         
    Fetched 178 kB in 0s (204 kB/s)                                                
    Reading package lists... Done
    tyler@tyler-ubuntu:~$ sudo apt-get install nvidia-381
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    E: Unable to locate package nvidia-381

```

Additional outputs:


```
    tyler@tyler-ubuntu:~$ cat /etc/lsb-release
    DISTRIB_ID=Ubuntu
    DISTRIB_RELEASE=17.04
    DISTRIB_CODENAME=zesty
    DISTRIB_DESCRIPTION="Ubuntu 17.04"
    tyler@tyler-ubuntu:~$ apt-cache policy nvidia-381
    N: Unable to locate package nvidia-381

```

---

### Post by oldos2er on 2017-08-29
According to the thread you linked to, the proper command to install 381 is ```
sudo apt-get install nvidia-graphics-drivers-381
```

---

### Post by Bashing-om on 2017-08-29
tbrady85; Hey ;

Make that add-apt-repository command as:
```

sudo add-apt-repository ppa:graphics-drivers/ppa

```
Then:
```

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-381
sudo reboot

```

should workie.

[INDENT][INDENT]Uh Huh
[/INDENT][/INDENT]

---

### Post by tbrady85 on 2017-08-29
> **Bashing-om said:**
> tbrady85; Hey ;

Make that add-apt-repository command as:
```

sudo add-apt-repository ppa:graphics-drivers/ppa

```
Then:
```

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install nvidia-381
sudo reboot

```

should workie.
[INDENT][INDENT]Uh Huh
[/INDENT]
[/INDENT]


Yeah I tried that, I should have updated the original code in my posting.  If you look at the output that I posted you'll see that I used "sudo add-apt-repository ppa:graphics-drivers/ppa" to install the repo.  As you can see in the output I still received the "unable to locate package nvidia-381"

---

### Post by tbrady85 on 2017-08-29
> **oldos2er said:**
> According to the thread you linked to, the proper command to install 381 is ```
sudo apt-get install nvidia-graphics-drivers-381
```

If you read the replies to that answer someone posted a link to the repo where you could see that the actual command is ```
nvidia-381
```
Either way I tried both commands and got the same results.

Whats even more confusing is that Pilot6, who was helping me on stack exchange, was running the exact same commands I ran in my output posted above, but it was installing for them so I know its a local issue on my system somewhere.  

And this may help narrow it down but I can install other packages fine. Its just with the nvidia drivers.  No matter what version of the driver I try to install I get the unable to locate package error.  Its almost as if my system isn't reading that repo for some reason.  ](*,)

---

### Post by deadflowr on 2017-08-29
What does
```
apt-cache search nvidia | grep 381
```
show?
Also what does the output for the 
```
sudo apt-get update
``` 
show.
Any errors?

---

### Post by tbrady85 on 2017-08-29
> **deadflowr said:**
> What does
```
apt-cache search nvidia | grep 381
```
show?
Also what does the output for the 
```
sudo apt-get update
``` 
show.
Any errors?

```
apt-cache search nvidia | grep 381
```

Doesn't return anything. It just goes back to a command line and

```
sudo apt-get update
``` 

doesn't return any errors. I have the output for that listed in the original post.



Just a quick update.  I'm able to run and install

```
sudo apt-get install nvidia-375
``` 

drivers fine but if I try to install any other driver versions I receive "unable to locate package" again.

---

### Post by Bashing-om on 2017-08-30
tbrady85; Humm ...

Partners repository NOT enabled in software sources ?? 

EFI machine - where secure boot needs disabling to install additional softwares ?

[INDENT][INDENT]just a maybe
[/INDENT][/INDENT]

---

### Post by deadflowr on 2017-08-30
Looking at the apt-get update output it seems strange to me that it Hit the repo but did not get the information from the repo.
I would have expected it to download the package information, at least the first time.
Somehow it seems like it did not.

I also wonder if there are conflictions between the graphics-drivers and xorg-edgers ppas.

Perhaps also try re-running the update command, as well as running the upgrade command
```
sudo apt-get update && sudo apt-get dist-upgrade
```
Just to be on the safe side so that the system it fully up-to-date.

**dist-upgrade only updates the current system, and does not upgrade the system to a new version of Ubuntu, for the record.

---

### Post by tbrady85 on 2017-08-30
Bashing-Um, I verified that the repository was enabled in the software sources and secure boot is disabled.

deadflowr, I know.  I'm completely lost with this.  I removed the xorg-edgers ppas and ran the install again with the upgrade command like you suggested but I'm still getting the "unable to locate package".  

:confused::confused::confused:

---

### Post by tbrady85 on 2017-08-30
Ok,

I just wanted to update everyone that the problem is solved.  When I followed Bashing-Um's suggestion of making sure that I had the PPA enabled, I noticed that the graphics-drivers PPA was listed several times (duplicates) in software & updates.  I removed all of the PPA's related to graphics-drivers and started the install over from scratch.  After doing that it finally located and installed the nvidia-381 driver. Not sure why it did this but none-the-less it worked. Thanks for the help everyone!

---

### Post by Bashing-om on 2017-08-31
tbrady85; Great !

Pleased you found the fix.
As this situation is now under control;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

