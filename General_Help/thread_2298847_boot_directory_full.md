---
title: "/boot directory full"
date: 2015-10-14
forum: General Help
---

### Post by asearle on 2015-10-14
Hallo,

I am running Lubuntu 14.04.03 but have a problem with updates:  The updates install fine but they leave files in the /boot directory which, after a while becomes full and has to be emptied manually (logging on as Sudo).  This is mildly irritating for me (who can do it) but impossible for friends of mine for whom I have installed Lubuntu on their PCs.

I enquired before and tried several things (including apt-get autoremove) but nothing worked.

The perfect solution would be if I could set an option which cleans out all but the newest of the update files in /boot.  Is this possible?

Many thanks to anyone who can help.

Regards,
Alan

---

### Post by sudodus on 2015-10-14
I think it might be risky to do this cleaning automatically, but [Ubuntu Tweak](https://askubuntu.com/questions/75454/how-do-i-install-ubuntu-tweak) is a tool, that helps you doing it. Use the ***Janitor*** (in Ubuntu Tweak).

Open the terminal. Add the required repository with the command:

```
sudo add-apt-repository ppa:tualatrix/ppa
```

Update the software list with the command:

```
sudo apt-get update
```

Finally, install Ubuntu Teak with the command:

```
sudo apt-get install ubuntu-tweak
```

After that, open dash (in standard Ubuntu) and type "ubuntu tweak" or find it via the menu in the other Ubuntu flavours.

---

### Post by echotech2 on 2015-10-14
I'm not the original poster.

  This is what I get?

```
dave@scamper:~$ sudo add-apt-repository ppa:tualatrix/ppa
[sudo] password for dave: 
 The official Ubuntu Tweak stable repository
 More info: https://launchpad.net/~tualatrix/+archive/ubuntu/ppa
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpzahhb10t/secring.gpg' created
gpg: keyring `/tmp/tmpzahhb10t/pubring.gpg' created
gpg: requesting key 0624A220 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpzahhb10t/trustdb.gpg: trustdb created
gpg: key 0624A220: public key "Launchpad PPA for TualatriX" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

```
 
  And from sudo apt-get update:

```
  W: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/vivid/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/vivid/main/binary-i386/Packages  404  Not Found
```

  Where did I go wrong?

---

### Post by sudodus on 2015-10-14
@echotech2

Maybe 'only' a temporary error. I tried now to install Ubuntu Tweak into a live system based on

lubuntu-14.04.3-desktop-amd64.iso

(so with no other tweaks)

and it worked without any problems.

-o-

You are running Vivid (15.04). Maybe there is no Ubuntu Tweak for that version.

---

### Post by cobalt2 on 2015-10-14
I looked up the ppa on Launchpad, and it is active. The Cannonical Server is probably down. Try again later.

---

### Post by howefield on 2015-10-14
> **echotech2 said:**
> Where did I go wrong?

Possibly when you tried to use a non existent vivid repository.

Looks like the last supported release in that ppa is Trusty.

---

### Post by echotech2 on 2015-10-14
> **howefield said:**
> Possibly when you tried to use a non existent vivid repository.

Looks like the last supported release in that ppa is Trusty.

```
 W: Failed to fetch http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/vivid/main/binary-amd64/Packages  404  Not Found
```


  But..but... but.  Wouldn't this indicate that the Vivid repository does exist?

---

### Post by sudodus on 2015-10-14
Ubuntu's vivid repositories exist and work. But the ***tualatrix*** PPA has not provided a version for vivid, only for trusty.

There are other tools to use for the same purpose. You can use ***synaptic***. It is a good idea to keep the ***two*** most recent kernels.

---

### Post by mcduck on 2015-10-14
No, that indicates that the *server* (ppa.launchpad.net) exists, but the rest of the URL is incorrect and doesn't point to an existing file on that server. Which would be because the repository doesn't have packages for vivid, so the *tualatrix/ppa/ubuntu/dists/vivid* directory doesn't exist.

Just go to [https://launchpad.net/~tualatrix/+archive/ubuntu/ppa]("https://launchpad.net/~tualatrix/+archive/ubuntu/ppa") and check the dropdown box for filtering by Ubuntu version, and you'll see Trusty is the last version available.

Anyway, simple "sudo apt-get autoremove" should uninstall old kernel versions, excluding the current one and one before that. And unless you know you really need it (because of full-disk encryption or something), I'd recommend against using a separate /boot partition.

---

### Post by howefield on 2015-10-14
> **echotech2 said:**
> But..but... but.  Wouldn't this indicate that the Vivid repository does exist?

I don't follow your line of thinking, when you add a ppa like

```
sudo add-apt-repository ppa:tualatrix/ppa
```

a new file is created in /etc/apt/sources.list.d/ based on the PPA name and the name of your Ubuntu release eg, in this case it would be :  

```
/etc/apt/sources.list.d/tualatrix-ubuntu-ppa-vivid.list
```

the file contains 

```
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu vivid main
# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu vivid main
```

The ppa "address" come from the ppa and the ubuntu version comes from your pc. You could replace the version name "vivid" with "trusty" and it would then work. I always check out ppa launchpad pages before adding just to make sure they contain what I expect them to.

Anyway, back on topic, it would seem fine for the OP as s/he is on Trusty :)

---

### Post by ian-weisser on 2015-10-14
> **asearle said:**
> The updates install fine but they leave files in the /boot directory which, after a while becomes full and has to be emptied manually

Older kernels in /boot are marked as eligible for autoremoval by /etc/kernel/postinst.d/apt-auto-removal, provided by the 'apt' package, and included with every apt (non-Snappy) install of Ubuntu.
Perhaps you have encountered one of several bugs that affects some users.
If so, be aware that your bug workaround should be temporary - if your bug is fixed, autoremoval may work properly without your workaround.

The most common sufferers of this bug use a separate /boot partition, required for LVM or full-disk encryption. An easy workaround for most laptop users is to simply leave those options unchecked when installing.

> **asearle said:**
> The perfect solution would be if I could set an option which cleans out all but the newest of the update files in /boot.  Is this possible?

It possible, though I recommend retaining one previous working kernel so a bad update doesn't leave your system unbootable.
The 'unattended upgrades' package has a setting that will happily run 'autoremove' for you each day, triggered by apt's normal cron.daily job.
Assuming your workaround simply marks older kernel packages as eligible for autoremoval (like the apt-auto-removal script does), that's all you usually need. 



If you develop your own solution, be sure to work with the package manager. Fighting apt is a good way to break your system in new and interesting ways.

---

### Post by asearle on 2015-12-03
This is the original poster here ...

I will experiment with Ubuntu Tweak but, from all the traffic here, it seems complicated (at least to install).

Really, I was hoping that Ubuntu (or rather "Lubuntu") would have picked up this problem and put some house-keeping in to handle it(?)

Is this not the case?  Does 15.10 still have the problem?

Thanks,
Alan

---

### Post by ian-weisser on 2015-12-03
It is not a problem most of us encounter. For example, In my decade with Ubuntu, I have not had the problem.
Nobody on the several bug reports has yet been able to explain why some suffer the problem and others don't.
Nobody has been able to explain yet how to reliably reproduce the problem on a fresh install.
We know there is a correlation with separate /boot partitions...but that's not causation.
That makes it difficult to fix.

---

### Post by sudodus on 2015-12-03
There *should* be no problems to install Ubuntu Tweak in 14.04 LTS according to post #2 (but the ppa for Ubuntu Tweak has no entry for 15.10).

---

### Post by asearle on 2015-12-12
Hallo Everyone,

I am a bit astonished that there is a thread about this topic at all, let alone a thread where there is all kinds of doubt about the solution.

In my view Lubuntu should clean up its own "previous versions" so as to not block the /boot directory.  Or the /boot directory should be much bigger!

With "Windows-8 discomfort" and now Windows-10 a whole stack of friends of mine want to try Linux.  Here I am recommending "Lubuntu" because the menus are very much like Windows-XP.  Ex-windows users seem to REALLY like that. But I feel like a fraud because, after several months happy and stable use, these friends come back to me complaining that they can't load updates and this is almost always because the /boot directory is full.

Arrrggghhh!

Why, yes why, can't Lubuntu fix this?

Regards,
Alan

---

### Post by sudodus on 2015-12-12
The standard way to install Lubuntu is to make one big root partition and one swap partition. This method will allow for many old versions of the kernel, because /boot is 'only' a directory in the big root partition.

But it is certainly a problem when there is a separate boot partition, for example in the case of 'encrypted disk'.

I suggest that you help the Lubuntu community by creating a convenient tool to remove old kernels (leaving only the two newest versions) :-)

---

### Post by vasa1 on 2015-12-12
> **asearle said:**
> ...

Why, yes why, can't Lubuntu fix this?

Regards,
Alan

Lubuntu 14.04.3 user here. No problems with */boot* filling up for me. *sudo apt-get autoremove* works just fine leaving me with two, sometimes three, kernels.

I suspect you've done something that's preventing autoremove from working.

BTW, _all_ *buntu flavors as the same in this respect.

---

### Post by Dennis N on 2015-12-12
I would say using Ubuntu or other distros in its family does require some user involvement and awareness in system maintainance. In your car, you may need to check the oil level and tire pressure from time to time. 

Things vary between distros too. There are other Linux distributions that in fact don't normally recommend kernel upgrades in their "recommended" updates. I have one of those installed on a laptop, and have yet to see a recommended kernel update in it's update manager, and if you always did what is recommended in that regard, would stick with only one kernel - the one that was originally installed! I'm not saying doing so is a good idea, but the head developer of that distro has such a policy.

I know of another well known distro that doesn't tell you about any available upgrades - no update notifier! They expect you to check periodically - even more demanding.

---

### Post by asearle on 2016-02-28
I believe that, yes, I should have left LVM unchecked during installation.  I will do this in future and then, with no extra boot partition installed (as is needed for LVM) there should be no problem.  Yippeee!

But I have installed Ubuntu on several friend's computers and it is very embarrassing that after a while Update stops working (as the boot directory is full).  They phone me up and then I have to either explain or go over and fix it for them  :-(

I wanted to permanently fix this by significantly expanding the /boot directory using a live GPartEd CD but found that the disk-sizes were not editable.

What do you guys recommend?  Should I be able to resize the partition(s)/boot-directory?  And which would be the best tool(s) to use?  Or is this generally a bad idea which might completely mess things up?

Or maybe there is an official Ubuntu-fix in the pipeline?

Many thanks,
Alan Searle
Cologne, Germany

---

### Post by ian-weisser on 2016-02-28
We found the problem. It's fixed in 16.04.

A fresh install of 16.04 should no longer accumulate old kernels.
For older releases of Ubuntu, enabling autoremove in /etc/apt/apt.conf.d/50unattended-upgrades should permanently prevent new accumulation of old kernels for most users.

---

