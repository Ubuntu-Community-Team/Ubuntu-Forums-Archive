---
title: "I am having trouble with apt and HandBrake that I could use help with"
date: 2012-10-21
forum: General Help
---

### Post by NoSalt on 2012-10-21
Hello All

    I am having an issue with apt and upgrading HandBrake. First my info:

Hardware: Dell PowerEdge T110 with 4GB of memory
Software: XUbuntu 12.04

I have HandBrake installed on my computer with the following lines in my /etc/apt/sources.list

```

deb [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) precise main
deb-src [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) precise main

```

Which I got from the HandBrake website ( [https://launchpad.net/~stebbins/+archive/handbrake-releases](https://launchpad.net/~stebbins/+archive/handbrake-releases) ). Whenever I attempt an "apt-get update" I get the following errors:

```

W: Duplicate sources.list entry [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/) precise/main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_stebbins_handbrake-releases_ubuntu_dists_precise_main_binary-amd64_Packages)

W: Duplicate sources.list entry [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/) precise/main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_stebbins_handbrake-releases_ubuntu_dists_precise_main_binary-i386_Packages)

W: You may want to run apt-get update to correct these problems

```

and

```

dpkg: warning: parsing file '/var/lib/dpkg/status' near line 32883 package 'handbrake-gtk':
 error in Version string 'svn3918ppa1~lucid1': version number does not start with digit

dpkg: warning: parsing file '/var/lib/dpkg/available' near line 34238 package 'handbrake-gtk':
 error in Version string 'svn3918ppa1~lucid1': version number does not start with digit

```

However, I don't have duplicate lines in sources.list, and whenever I run "apt-get update" to correct the problem, I get the same errors.

Has anybody come across this that can help me out?

Thanks for taking the time to read, and have a great day.    :)

---

### Post by NoSalt on 2012-10-22
Bump

---

### Post by yurfader on 2012-10-22
I was able to install handbrake in xubuntu in tho following way.

From the terminal.
1.- Addeed the repository.
```
sudo add-apt-repository ppa:stebbins/handbrake-snapshots
```2.- Installed synaptic
```
sudo apt-get install synaptic
```3.- Execute synaptic with
```
sudo synaptic
```and open the repositories option in synaptic and in the tab with other sources select the line with the handbrake name in it and change the quantal option to precise option. Uncheck the option for sources.
4.- Install handbrake-gtk form synaptic or from the terminal once the repositories are updated.

In your case, the first think that I would do is to install synaptic and see how the repositories look like. And if you see double lines for the same repositories delete them or unselect them.

Hope this helps.

---

### Post by howefield on 2012-10-22
You have both 32 and 64 bit handbrake repositories in there, try taking out the one you don't need.

---

### Post by NoSalt on 2012-10-22
howefield, how do you know I have both of these entries. The two lines I have provided (that are in my /etc/apt/sources.list) do not show this. What are you basing your statement on?

thanks

---

### Post by howefield on 2012-10-22
> **NoSalt said:**
> howefield, how do you know I have both of these entries.

You posted it.

---

### Post by NoSalt on 2012-10-22
howefield

    Yes, those are the errors I am getting, but I have only the two lines in my /etc/apt/sources.list file. Nowhere did I enter any information for the two different architectures.

```

deb http://ppa.launchpad.net/stebbins/ha...eleases/ubuntu precise main
deb-src http://ppa.launchpad.net/stebbins/ha...eleases/ubuntu precise main

```

---

### Post by lrgmmc on 2012-10-22
I'd remove the entries from source.lst then rerun apt-get update. After which add the repo via add-apt-repository ppa:stebbins/handbrake-snapshots as yurfader said.

---

### Post by NoSalt on 2012-10-22
Ok ... I tried yurfader's method and it worked great ... thanks!

I had an issue with this step:

"open the repositories option in synaptic and in the tab with other sources select the line with the handbrake name in it and change the quantal option to precise option. Uncheck the option for sources"

I didn't see any "quantal" option, I did see a line in the "Edit Source" window that said "Distribution: precise". However, it seems like everything is settled out. I updated my sources, and installed handbrake, and it worked great.

Thank you everybody who read, and thank you to howefield and yurfader for their help.

Have a great day.   :-D

---

### Post by lrgmmc on 2012-10-22
Glad to hear. Can you set this thread as solved.

---

### Post by NoSalt on 2012-10-23
Just as a quick final note, what I did:

1. Deleted all HandBrake instances from /etc/apt/sources.list
2. Deleted all HandBrake instances from /etc/apt/sources.list.d/
3. I had recently updated versions of Ubuntu from 10.04 to 12.04, so I deleted all of the prior files in /etc/apt ... they were pretty clearly annotated as "not used" by the upgrade process.
4. Followed yurfader's advice, except I added the following 2 steps after his step #3.
    4a. > sudo apt-get update
    4b. > sudo apt-get upgrade
5. Win!

Again, thanks to all who helped.

---

