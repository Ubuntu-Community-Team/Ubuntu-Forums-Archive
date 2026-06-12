---
title: "Custom Installation/Live .ISO image creation. Recommendations?"
date: 2022-11-19
forum: General Help
---

### Post by ne29914 on 2022-11-19
Hi.
I have the task of maintaining a set of of laptops (12), that are quite alike but only to 75%. This means that carrying a system backup (rsync, dd, whatever) from one to the other doesn't work.
I'd like to use a live-boot image (.iso) for upgrades/changes etc. instead. This would give me a universal solution, also for newly incoming laptops.

I've looked around and found:

Ubuntu Customization Kit.
Cubic.

Does anyone have experience with either or have other/better suggestions?

Thanks.

---

### Post by TheFu on 2022-11-20
I have about 20 systems to deal with.
I do a base install with only ssh+fail2ban to start.  Then I use ansible to load and configure everything else. 

Sure, I wanted to do custom automatic installs, but the systems are all slightly different, some are snowflakes and Canonical keeps screwing up the auto-install stuff both on servers and desktops.  

A base install takes between 8 and 15 minutes). I have a read-only NFS share that I use to pull over my core settings to each system "deploy423943xyz" account setup for sudo without password ... stuff like ~/.bashrc and ~/.bash_aliases and a few scripts to grab my public ssh keys quickly.  Then I point my ansible base playbook at the system and push 
* time sync
* DNS
* apt-cache
* postfix satellite setup including aliases for root, deploy, etc.
* logwatch
* rdiff-backup and some other system config stuff (inxi, lshw). We use "pulled" backups, so I have to modify the backup server and setup a special backup account. We don't really let people have any local storage, except on laptops. I want to minimize data stored on desktops to be only temporary stuff.
* autofs settings for nfs mounts when they are on the network and to handle CDROMs. I also setup a DAVFS for access to the nextcloud storage.

During the install, I setup LVM in specific ways to supporting future needs easier. That is mostly scripted now and uses less than 100G of storage by default. Of course, the LVM partition takes all the storage after the boot and grub areas are created, so we can extend an LV as needed.  I've never been brave enough to allow LVM's automatic extend methods to control it.  Logwatch includes storage warnings, so we aren't surprised.

In theory, Cobbler is a way to deploy/install systems, but I wasn't ever able to get it working, then a local University had a Cobbler incident that wiped over 500 desktop computers, loading 100% fresh OS.  Ooops.  I'll keep my mistakes confined to ansible.

I also handle the weekly patching and Ansible could do that, but a simple ssh script does it and is more flexible.  'deploy' accounts are handy. That is one of the best things I've done. Some systems need some specialized updates, so those are handled by the script too.  For example, we get DNS block lists for nasty parts of the internet and to block access to most social media sites, except by the marketing guys. Those lists are constantly changing, so each week, we pull the new list of domains to be blocked and integrate them into our DNS.

Of course, there isn't any perfect solution for everyone. We each need to find what works for us. Maybe these ideas can help or you'll point out easier ways for us to do it better.
If the system was already owned by a user, we'd start with a fresh OS install, then selectively restore from backups.  This selective restore gets them a working system that was like the old one, with their local data, local settings, and nearly all prior programs (if not all prior program) installed in about 30-45m worst case.  We've used it for moving LTS-to-LTS releases too.  We can usually fit 2 OS upgrade in a day, while handling other stuff too, but that happens seldom, so we can work with the user for how and when they want to do it.  We're small enough to be flexible.  

We've been mostly remote (everyone) for years now, but I do miss having direct console access during these OS migrations.  I need to get 1-2 pikvm devices to make it so I can do everything remote, except insert a flash drive into the system.  The pikvm does support accessing my USB ports into the remote system, at least I've heard that.  Not sure I want to do remote installs that way when almost any ventoy 16G flash drive can hold tools and 3 distros easily.

---

### Post by ne29914 on 2022-11-20
Thanks for your input.
Ideally, I'd like to create an install image that does the "normal" OS install as well as the program/application/settings install.
But I have no problem doing it in two steps with first an OS install followed by the "personalized" install.
Time is not an issue, and setting up the machines in parallel using multiple boot media is easy.

I wll take a close look at Ansible and come back with my result in a few days.

Thanks again.

---

### Post by ne29914 on 2022-11-20
OK, looked at Ansible documentation, and it's not what I need/want.
I'm back to Cubic and the Customization Kit, which will do what I want (live-boot .iso with all user programs etc. embedded)..

What I have NOT found is a tool for generating a "second-level" installation file/.iso for the user programs and settings only. It apparently does not exist (or my search terms are wrong).
This would be my preferred solution though, avoiding a full OS install for every change to the user program/setting list.

Thanks, any suggestion very welcome.

---

### Post by oldfred on 2022-11-20
I just use standard scripts for new install. 
Some cases I restore my /home configuration which has all my settings, others I want to test, experiment and do not reinstall my /home.
I have just installed .config from /home which did most of my settings.
I export list of installed applications and/or have a bash script with the default list of apps that I want.

My rsync backup script file includes this also. The dpkg list is a very long text list of all applications and the dependencies. 
If upgrading, you may want to edit it to remove obsolete, old kernels or others. It will not re-install anything already installed.
[https://help.ubuntu.com/community/ReinstallingSamePackages](https://help.ubuntu.com/community/ReinstallingSamePackages)
You can also export list of manually installed apts and use that to reinstall.
apt-mark showmanual | sort -u

My bash script has multiple lines like this. I do not like one very long line, but then have to review & press enter to accept. I do not want auto y.
/usr/bin/apt-get install aptitude gawk calibre fdupes git inxi k3b

---

### Post by ne29914 on 2022-11-20
@oldfred,
I was mulling the idea of a script, but had no reference. Your link is good, I'll pursue that. It will take me part of the way (installation), but does not solve the configuration files issue.

Thanks.

---

### Post by oldfred on 2022-11-20
Your /home has all your configuration files usually in . or hidden files.
If you set one up the way you want, then copy /home over it will be the same.
Your /home without data is tiny as the configuration files are not large.

My /home which now has lots of data in Firefox & Thunderbird, .cache is something you do not backup and .config is most of the user configuration. But some apps have their own . files with configuration info.
```
[FONT=monospace][COLOR=#ffffff]                                                          [/COLOR][COLOR=#000000] [/COLOR]
--- /home/fred -------------------------------------------------------------------------------------------------------------- 
[COLOR=#ffffff]  640.6 MiB [##########] /.cache                                                                                             [/COLOR][COLOR=#000000] [/COLOR]
  420.2 MiB [######    ] /.mozilla 
   22.8 MiB [          ] /.local 
    8.5 MiB [          ] /.config 
    1.0 MiB [          ] /rpCalc 
  592.0 KiB [          ]  .xsession-errors 
   80.0 KiB [          ] /.thunderbird 
   76.0 KiB [          ] /.pki 
   52.0 KiB [          ]  system-info 
   36.0 KiB [          ]  .bash_history 
   24.0 KiB [          ]  system-info.txt 
   24.0 KiB [          ] /.aqbanking 
   20.0 KiB [          ] /Desktop
[/FONT]
```

---

### Post by TheFu on 2022-11-20
> **ne29914 said:**
> @oldfred,
I was mulling the idea of a script, but had no reference. Your link is good, I'll pursue that. It will take me part of the way (installation), but does not solve the configuration files issue.

Thanks.

Which is what ansible is expert at handling, but if you've looked and decided against it, so be it.  I fear you found the marketing documents about ansible, not the beautiful, clean, CLI interface that does everything.  Management likes fancy webapps that make pretty diagrams and big "OK" buttons.  None of that is needed and just mucks up the tool, IHMO.

---

### Post by C.S.Cameron on 2022-11-21
I prefer installing .img files instead of ISO files.
You can use most of the same tools to install: Rufus, Etcher, dd, Gnome-Disks, mkusb, etc.
See: [https://askubuntu.com/questions/1300540/how-to-duplicate-a-ubuntu-system-for-distribution](https://askubuntu.com/questions/1300540/how-to-duplicate-a-ubuntu-system-for-distribution)
When creating the source OS avoid installing proprietary drivers, (Nvidia, etc).
If the source OS is UEFI, do not try to install it's image on a Legacy computer.

---

### Post by TheFu on 2022-11-21
For dealing with images, fsarchiver creates a compressed image - it is better if it understands the file system, since it won't blindly grab unused space. 

It can be used to grab an entire disk or partition or just a file system.  Lots of tools can do that, so it isn't anything special.  What makes fsarchiver different is that it can restore to smaller targer partitions, if the data in the partition will fit. 

Just something else to consider if images are used.

---

### Post by ne29914 on 2022-11-21
@oldfred: yes, adding an extra step to copy the /home configs would be an option that I can accept. This would also give users an initial Desktop.
@TheFu: "[COLOR=#000000]I fear you found the marketing documents about ansible," You are probably right. It presented itself as every sysadmin's wet dream of remotely controlling and setting up 100s of users plus other magic, which is way overblown for me.
@C.S.Cameron: I doubt that it would work. The machines are not the same, so the safest seems to be a file-based install, not an image-based one.

Preliminary plan of action:
1: basic OS install.
2: script to install the application programs plus copy a /home fileset to the target machine.
I'll still need to do a few more things (like setting UMASK etc.), but that's details.
How's that look?

Thanks All. I'll put on my thinking hat. All inputs still welcome.[/COLOR]

---

### Post by TheFu on 2022-11-23
> **ne29914 said:**
>  
@TheFu: "[COLOR=#000000]I fear you found the marketing documents about ansible," You are probably right. It presented itself as every sysadmin's wet dream of remotely controlling and setting up 100s of users plus other magic, which is way overblown for me.


Actually, it does exactly that. The setup is fairly trivial.  1 system is the "deployment server" ... or workstation ... or whatever you want to call it.  It uses ssh with either passwords or ssh-keys to connect to each of the other systems run run "desired state" instructions.  The difference between 5 systems and 5000 really isn't much.  We can specify systems by exact dnsname, subnet, or pattern of dns-names.
* db01 - db99.
* 10.232.1.20-.237
* or just by name.
Different groupings of hosts are possible, say you have a base set of tool you want on every system, period.  Desktops, servers, whatever.  That would be my "all" group.  They call this an inventory.
Then I'd have different groups for desktops and server and perhaps different types of servers.   Just depends on what you need.  We can always point at an individual system. Always.

When I suggested you'd hit some marketing stuff, I suspected you'd found a webapp and 20 pages of how to install it.  None of that is needed.   I've never used that method and don't want to.  I typically run commands like:
```
$ ansible-playbook  some-playbook-that-does-something.yml
```
I have playbooks for all sorts of things, which are made up of tasks, roles, and variables.  Think of a playbook as a program.  A role as what the target machines purpose is and the tasks as small chunks of things that need to be installed/configured.  It isn't necessary to have a playbook or roles. Also, we can setup the organization anyway we like, but there is a directory hierarchy that is suggested to help keep things organized.  Just starting out, create a task that does 1 simple thing and run that task against a group of computers in your inventory file. That would be something like:

```
$ ansible tasks/logwatch.yml cur
```

Unlike every other devops tool I know, ansible doesn't have magical directories For stuff. the tasks/logwatch.yml file above is in the relative directory "tasks" just below the CWD.
"cur" in my inventory of all current systems.  the playbook which does the same thing is run:
```
$ ansible-playbook plybk-push-logwatch_update.yml
```

Again, since my Ansible version is old, a new install probably won't work with this exact structure, but here's that playbook:
```
$ more plybk-push-logwatch_update.yml 
---
- name: Push Logwatch Settings and Script Update
  hosts: cur
  sudo: True
  vars:
    DEBIAN_FRONTEND: noninteractive
  vars_files:
    host_vars/key_infrastructure.yml

# #####################################################################
  tasks:
  - include: tasks/logwatch.yml
```

And the logwatch.yml task file:
```

---
- name: Install logwatch
  package:
    name: logwatch 
    state: present

- name: Make logwatch mail {{ logwatch_email }} daily
  lineinfile:
    path: /etc/cron.daily/00logwatch 
    regexp: "^/usr/sbin/logwatch" 
    line: "/usr/sbin/logwatch --output mail --mailto {{ logwatch_email }} --detail low" 
    state: present
    create: yes

- name: Logwatch local df options
  copy: 
    src: files/etc_logwatch_conf_services_zz-disk_space.conf
    dest: /etc/logwatch/conf/services/zz-disk_space.conf
    mode: '0644' 
    owner: root
    group: root
```

Once you are used to the yaml, it really becomes fast.  I'd forgotten that I customized the disk_space reporting for logwatch so I didn't have to see any loop devices, ever.  Handy to have that easily solved for all systems by running 1 command.

The requirements on the target systems generally already exist.   ssh, deployment userid, some core python modules. A minimal Ubuntu desktop or server has them.

> **ne29914 said:**
>  
Preliminary plan of action:
1: basic OS install.
2: script to install the application programs plus copy a /home fileset to the target machine.
I'll still need to do a few more things (like setting UMASK etc.), but that's details.
How's that look?

Thanks All. I'll put on my thinking hat. All inputs still welcome.

Nothing wrong with scripting.  Rather than using Ansible, by weekly patching uses an ssh script.  It is smart to realize when the solution is more complex than needed.  While I could use ansible to handle patching, I think it would be overkill.  OTOH, if I wanted to have 10 systems patched concurrently, ansible makes that easier than manually handling it in ssh.

---

### Post by guiverc on 2022-11-25
I'll mention this, but I can only provide it as an idea.

I *volunteered* at [ComputerBank ]("https://www.computerbank.org.au/")'long ago'; a computer recycler that received donations of old computer hardware from corporations, *refurbished *it, then sold it (*very cheaply to those with pension type cards*) etc.

We had a *spec & check* stage where the drives were removed *(boxes not fit for re-use recycled etc*)... but eventually the boxes reached a *build* stage where the system was put in them.  That included the obvious (*getting RAM to an appropriate level & other hardware stuff*) plus adding a drive which contained our modified Ubuntu image.

We kept a *current* image which was just cloned from a 80GB clone-master to whatever size drives were put on the *cloning box* (*80GB or larger*). Any tweaks made would just get re-cloned to the clone-master (80GB) driveand thus end up cloned to the actual drives used in builds

We didn't install as stated,  When doing a  '*build*', I just grabbed the drive of a capacity I wanted from the pile of cloned drives(*ensuring drive had correct markings etc.. procedures to ensure we didn't boot anything we were given until post-DBAN, post-CLONE etc*), inserted it & when it looked good, it was booted the box & ensure it was all ran good.

We then performed our final *tweak* phase, where we verified everything was as expected on the *build*. All software we wanted existed on the image that was cloned onto the drives, and the most common issue I recall doing during this *tweak* phase related to *audio* configuration; to ensure our test media (DVD, CD, various movie files) all sounded good etc.  There were boxes where *graphics* drivers needed tweaking (*installing*) as well; but that was rare as our image included many nvidia & other closed-source modules anyway that covered most boxes. (*my memory could be hazy here though; needing to tweak video was rare & I just recall spending the time with stopwatch etc. doing testing to ensure no tearing & other issues that can occur but never needing to fix anything beyond audio on occasion*).  The *tweak* phase was mostly checking, then we moved to our final *pricing* where we'd complete the build sheet & price it.

CBV had created ISOs for installing, but just swapping a pre-prepared (*clone**d*) drive was just so quick  (*we had to have the box open anyway to do cap-scan & other visual checks; hey few boxes need screws for drives anyway if enterprise hardware that we tended to use* *so it fast*).

---

### Post by TheFu on 2022-11-25
> **guiverc said:**
>  ...
CBV had created ISOs for installing, but just swapping a pre-prepared (*clone**d*) drive was just so quick  (*we had to have the box open anyway to do cap-scan & other visual checks; hey few boxes need screws for drives anyway if enterprise hardware that we tended to use* *so it fast*).

I can confirm that moving a working OS HDD to a new system works. 

The only problem I've had doing that was with GPU drivers. So the official image should have F/LOSS video drivers enabled for the first boot, always. If you know the exact GPU, placing the drivers onto the image would be smart.

I've moved installed OSes from C2D to C2Q to Core i5 to Ryzen systems.  Sometimes the wired ethernet wouldn't work since systemd started naming the NIC without eth0, but we always use static IPs (self-inflicted problem).  People on desktops would likely use network-manager to discover the NIC and DHCP for network settings.  Clonezilla and fsarchiver are ways to clone drives or partitions. Both compress the source images that would be expanded as written to the devices.  Clonezilla can use a tiny stub and pull the images over the network. I suppose PXE boot could be used.  I've not done that except for play testing.  Heck, dd over a tiny linux (16MB total) with netcat+dd could be used to create a cloned install too.  Just be certain the OS partition/volume is large enough, since resizing later will be a huge pain if there is any other partition with data "to the right" of the OS partition.  You know this stuff.

---

### Post by HermanAB on 2022-11-25
Debian Preseed is the solution that you are looking for. It works and is easy to set up:
[https://wiki.debian.org/AutomatedInstallation](https://wiki.debian.org/AutomatedInstallation)

The magic is that Preseed will install identical working systems on differing hardware.

---

