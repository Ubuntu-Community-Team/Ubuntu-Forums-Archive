---
title: "No advanced options in boot menu?"
date: 2015-07-09
forum: General Help
---

### Post by cogset on 2015-07-09
I've installed Ubuntu MATE 15.04 and started to poke around, according to this wiki page  [https://wiki.ubuntu.com/SystemdForUpstartUsers#Switch_to_upstart_for_a_single_boot](https://wiki.ubuntu.com/SystemdForUpstartUsers#Switch_to_upstart_for_a_single_boot)  I should have a non-systemd boot option in the advanced boot menu, problem is I'm not seeing it: the only other option in that advanced menu is the recovery mode, and that's it.

Is Ubuntu MATE different from a standard 15.04 installation in this regard? I kinda assumed such basic things would not change, maybe some packages are missing?

---

### Post by ajgreeny on 2015-07-09
What you normally see in Advanced, is an **upstart** option, ie to use upstart, not systemd.

Do you have upstart installed in the mate version?

---

### Post by v3.xx on 2015-07-09
Your right, its not there.  Why? I do not know, but installing the upstart-sysv package will work just fine.

---

### Post by cogset on 2015-07-10
This is what I have installed  by default (in a clean installation):

```
~$ dpkg-query   -W  -f  '${Status}\t ${Package}\t  ${Version}\n'  systemd*|sort -k1
install ok installed     systemd          219-7ubuntu6
install ok installed     systemd-sysv     219-7ubuntu6
unknown ok not-installed         systemd-services         
unknown ok not-installed         systemd-shim     
unknown ok not-installed         systemd-ui
       
~$ dpkg-query   -W  -f  '${Status}\t ${Package}\t  ${Version}\n'  sysv*|sort -k1
install ok installed     sysvinit-utils   2.88dsf-53.2ubuntu12
install ok installed     sysv-rc          2.88dsf-53.2ubuntu12
unknown ok not-installed         sysvconfig       
unknown ok not-installed         sysvinit         
unknown ok not-installed         sysvinit-core    
unknown ok not-installed         sysv-rc-conf
     
~$ dpkg-query   -W  -f  '${Status}\t ${Package}\t  ${Version}\n'  upstart*|sort -k1
unknown ok not-installed         upstart          
unknown ok not-installed         upstart-bin      
unknown ok not-installed         upstart-sysv     
```


I've simulated the installation of **upstart-sysv**, but that would in turns remove **systemd-sysv**, as explained here [Permanent switch back to upstart]("https://wiki.ubuntu.com/SystemdForUpstartUsers#Permanent_switch_back_to_upstart") whereas I was trying to use take advantage of this other option[ Switch_to_upstart_for_a_single_boot ]("https://wiki.ubuntu.com/SystemdForUpstartUsers#Switch_to_upstart_for_a_single_boot")which apparently just isn't there, now I wonder if Ubuntu MATE 15.04 is somehow different in that regard from a standard  15.04 installation or if I can manually edit the boot command line for a one-time boot without systemd (assuming I can figure out the correct paramters).

It would useful at this point if someone using a standard 15.04 version could confirm that the [ Switch_to_upstart_for_a_single_boot]("https://wiki.ubuntu.com/SystemdForUpstartUsers#Switch_to_upstart_for_a_single_boot") option does indeed work.

---

### Post by ajgreeny on 2015-07-11
> **cogset said:**
> It would useful at this point if someone using a standard 15.04 version could confirm that the [ Switch_to_upstart_for_a_single_boot]("https://wiki.ubuntu.com/SystemdForUpstartUsers#Switch_to_upstart_for_a_single_boot") option does indeed work.
I do not have any useful comments about the first part of your post but I can certainly confirm that, even though my 15.04 is a VM running in VBox, I can change the init system from systemd to upstart from the grub menu for that single boot with no difficulty.

---

### Post by cogset on 2015-07-11
Thanks, so this option does indeed work in a standard 15.04 installation, whilst it doesn't (actually, it isn't even there) in Ubuntu MATE 15.04 . 

 If it isn't too much trouble, can you post which upstart packages do you have installed and how does the grub command line look when using the upstart boot option (I guess that  would be easily spotted looking in the grub.cfg file) ? 

  I still have some residual  hope that by manually editing the boot options I could maybe manage to boot with upstart instead of systemd, although I frankly doubt that if this were possible they would have simply  skipped adding this to the advanced boot options.

---

### Post by QDR06VV9 on 2015-07-11
> **cogset said:**
> This is what I have installed  by default (in a clean installation):

```
~$ dpkg-query   -W  -f  '${Status}\t ${Package}\t  ${Version}\n'  systemd*|sort -k1
install ok installed     systemd          219-7ubuntu6
install ok installed     systemd-sysv     219-7ubuntu6
unknown ok not-installed         systemd-services         
unknown ok not-installed         systemd-shim     
unknown ok not-installed         systemd-ui
       
~$ dpkg-query   -W  -f  '${Status}\t ${Package}\t  ${Version}\n'  sysv*|sort -k1
install ok installed     sysvinit-utils   2.88dsf-53.2ubuntu12
install ok installed     sysv-rc          2.88dsf-53.2ubuntu12
unknown ok not-installed         sysvconfig       
unknown ok not-installed         sysvinit         
unknown ok not-installed         sysvinit-core    
unknown ok not-installed         sysv-rc-conf
     
~$ dpkg-query   -W  -f  '${Status}\t ${Package}\t  ${Version}\n'  upstart*|sort -k1
unknown ok not-installed         upstart          
unknown ok not-installed         upstart-bin      
unknown ok not-installed         upstart-sysv     
```


I've simulated the installation of **upstart-sysv**, but that would in turns remove **systemd-sysv**, as explained here [Permanent switch back to upstart]("https://wiki.ubuntu.com/SystemdForUpstartUsers#Permanent_switch_back_to_upstart") whereas I was trying to use take advantage of this other option[ Switch_to_upstart_for_a_single_boot ]("https://wiki.ubuntu.com/SystemdForUpstartUsers#Switch_to_upstart_for_a_single_boot")which apparently just isn't there, now I wonder if Ubuntu MATE 15.04 is somehow different in that regard from a standard  15.04 installation or if I can manually edit the boot command line for a one-time boot without systemd (assuming I can figure out the correct paramters).

It would useful at this point if someone using a standard 15.04 version could confirm that the [ Switch_to_upstart_for_a_single_boot]("https://wiki.ubuntu.com/SystemdForUpstartUsers#Switch_to_upstart_for_a_single_boot") option does indeed work.
In the early development cycle you had to install
```
sudo apt-get install upstart
```
Which would also boot with upstart as default.
To get the option in grub>Advanced> 
To Choose Between upstart or systemd, but after release Date I'm not sure if that is an option or not.( I see ajgreeny has both so it is)
And in Wily(15.10) you won't have that option as it sets now! (maybe it will change by the time wily hit's prime time but I Doubt it.)
But try it.
Regards

---

### Post by cogset on 2015-07-12
That was it, installing the **upstart** package got me that missing advanced boot option ;) -thanks everybody for their help.

For some reason that package is not included in a standard Ubuntu MATE 15.04 installation, now I'm wondering if *there may a be* a valid reason after all, because if I boot with upstart everything works, except the shut down button (which is greyed out and non-responsive): to log out and/or reboot I have to use a terminal.
If I reboot with systemd it works again, so there's definitely some quirk here.

---

### Post by QDR06VV9 on 2015-07-12
upstart is being replaced by systemd.
From here [http://www.zdnet.com/article/after-linux-civil-war-ubuntu-to-adopt-systemd/](http://www.zdnet.com/article/after-linux-civil-war-ubuntu-to-adopt-systemd/)
> It was an ugly fight at times. On one side you had Ubuntu favoring its [Upstart program]("https://wiki.debian.org/Debate/initsystem/upstart")  to replace the old Unix/Linux init daemon, which oversees the operating  system's start-up and shutdown processes. On the other side, you had  the [Red Hat and SUSE supported systemd]("http://www.freedesktop.org/wiki/Software/systemd/").
 Finally, after                  [Debian, Ubuntu's parent Linux distribution, voted for systemd]("http://www.zdnet.com/article/debian-init-decision-further-isolates-ubuntu/")     , Ubuntu's founder Mark Shuttleworth announced that [Canonical]("http://www.canonical.com") would [support systemd]("http://www.markshuttleworth.com/archives/1316") rather than continue to push for Upstart.


Regards

---

### Post by grahammechanical on 2015-07-12
It was during the 26 week development period that the switch to systemd began. First, we got an advanced option for a systemd boot. Then the switch over was made and for a while we got an advanced option for an upstart boot. By the time 15.04 was released the switch over was finalized and the advanced option for upstart was removed. In this way there would be no need to maintain two init systems.

From what I read the ugly fight was between Debian developers some of whom did not like that systemd would turn into something a lot more than an init system. Some felt that the Redhat developers working on Debian were subverting the Debian mission and they decided to fork Debian and develop it independently.


[https://devuan.org/](https://devuan.org/)

[http://www.pcworld.com/article/2841873/meet-systemd-the-controversial-project-taking-over-a-linux-distro-near-you.html](http://www.pcworld.com/article/2841873/meet-systemd-the-controversial-project-taking-over-a-linux-distro-near-you.html)
[URL="http://www.pcworld.com/article/2841873/meet-systemd-the-controversial-project-taking-over-a-linux-distro-near-you.html"]


[/URL]

---

### Post by cogset on 2015-07-13
Well yes, I've read here and there about the systemd querelle, and Devuan, and [uselessd ]("http://uselessd.darknedgy.net/")and so on.
I may have an idea about this, but that's not what this post was about: I was just trying to understand if what is explained in [https://wiki.ubuntu.com/SystemdForUpstartUsers ]("https://wiki.ubuntu.com/SystemdForUpstartUsers")still applies, in order to switch between upstart and systemd and (hopefully) learn the differences.

I'm not sure how things stack up here, since the wiki  says > If you are running Ubuntu vivid (15.04), you can easily switch between upstart and systemd at will since both packages are installed at present. As of March 9 2015, vivid was changed to use systemd by default, before that upstart was the default.  and ajgreeny said he can indeed switch init systems in 15.04, but then you say > By the time 15.04 was released the switch over was finalized and the advanced option for upstart was removed

---

