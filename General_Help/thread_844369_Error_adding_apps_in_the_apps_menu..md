---
title: "Error adding apps in the apps menu."
date: 2008-06-29
forum: General Help
---

### Post by Nothingpp on 2008-06-29
W: Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/pool/main/g/glade-3/libgladeui-1-7_3.4.5-0ubuntu1_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/g/glade-3/libgladeui-1-7_3.4.5-0ubuntu1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/pool/main/g/glade-3/glade-3_3.4.5-0ubuntu1_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/g/glade-3/glade-3_3.4.5-0ubuntu1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/pool/main/k/kdesdk/kbabel_3.5.9-0ubuntu1_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/k/kdesdk/kbabel_3.5.9-0ubuntu1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

---

### Post by Nothingpp on 2008-06-29
> **Nothingpp said:**
> W: Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/pool/main/g/glade-3/libgladeui-1-7_3.4.5-0ubuntu1_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/g/glade-3/libgladeui-1-7_3.4.5-0ubuntu1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/pool/main/g/glade-3/glade-3_3.4.5-0ubuntu1_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/g/glade-3/glade-3_3.4.5-0ubuntu1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


W: Failed to fetch [http://nl.archive.ubuntu.com/ubuntu/pool/main/k/kdesdk/kbabel_3.5.9-0ubuntu1_i386.deb](http://nl.archive.ubuntu.com/ubuntu/pool/main/k/kdesdk/kbabel_3.5.9-0ubuntu1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

Note i get this error setup everywhere when i install, when i change the menu, when i update..

---

### Post by Elfy on 2008-06-29
Has this always been a problem for you. Might be able to help - can you open a terminal and run these 2 commands for me. In accessories if you've not used it yet.

```
cat /etc/hosts
cat /etc/hostname
```

---

### Post by Nothingpp on 2008-06-29
It worked b4..

127.0.0.1 localhost
127.0.1.1 stefan-ubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


stefan-ubuntu

---

### Post by Elfy on 2008-06-29
It's not that then :) they look fine.

I tried one of the deb lines you have trouble with and connected ok.

If it worked before, what have you done in the meantime?

You can try to set your repo to the main server rather than the nl one - open software sources and change the server to main server and try to reload.

It looks to me like it's trying to get the repo from you.

---

### Post by Nothingpp on 2008-06-29
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Elfy on 2008-06-29
> If it worked before, what have you done in the meantime?

Have you installed anon-proxy or soemthing similar?

---

### Post by Nothingpp on 2008-06-29
-- On my windows dual booted now
Cuz ubuntu wasn't loading this page
--

Yea i installed anon-proxy or atleast some kind of proxy

---

### Post by Elfy on 2008-06-29
Ok that is what is causing the error then, I don't know how to set it up though unfortunately.

You will have to search for how to set it up. There is probably a man page for it which might help you - use in aterminal 

```
man anon-proxy
```

perhaps, not sure of it though.

If you can't get anywher with it and can't install anything you will have to remove it completely.

Sorry I can't be of more help.

---

### Post by Nothingpp on 2008-06-29
I have removed all the proxy's from my ubuntu, but it still doesn't work.

---

### Post by Elfy on 2008-06-29
I think that you need to completeley remove whatever you installed and then reboot - I have never used these sorts of apps so don't know what they do, but in the threads I found it necessitated a complete removal of the application itself.

You can do it through synaptic - make sure there are no residual configurations left behind from the status pane.

If you are not sure of the name of the software you installed - check the history - it's in the file menu I think.

---

### Post by cariboo on 2008-06-29
The proxy deamon is still running, in a terinal try:

```
ps ax | grep proxy
```

and see what you get. IF you get any results with proxy in it, just kill the process.

Jim

---

### Post by Nothingpp on 2008-06-29
well i kinda isntalled every thing that was on there so euhm... x]

---

### Post by Elfy on 2008-06-29
> **Nothingpp said:**
> well i kinda isntalled every thing that was on there so euhm... x]

You installed everything that was in synaptic :shock:

---

### Post by Nothingpp on 2008-06-29
yes.. lol ... i didn't know what i was doing

btw every thing with a ubuntu sign b4 is, are those the original packages, so the other ones are the extra ones?

---

### Post by Elfy on 2008-06-29
Oh my word - just out of interest how long did it take ?

---

### Post by Nothingpp on 2008-06-29
Euh about 10 hours Oo Left it on when i went to bed..

---

### Post by Elfy on 2008-06-29
I don't quite know what to suggest then, if you run the command that you got from cariboo907 what output do you get?



> Euh about 10 hours Oo Left it on when i went to bed..

:lolflag:

---

### Post by Elfy on 2008-06-29
> btw every thing with a ubuntu sign b4 is, are those the original packages, so the other ones are the extra ones?

Not necessarily - I have some not installed - but then I didn't install the whole of the repository :D

Edit 

I think you deserve a 

=D> =D> =D> =D> =D> =D>

---

### Post by Nothingpp on 2008-06-29
now slowly removing things that i installed

---

### Post by Elfy on 2008-06-29
Yea hang on - there might be a way to run something to do it for you if you really did install the whole of the repos.

Alternatively it would probably be quicker to do a reinstall assuming you haven't done much in the way of setting up apps etc.

I guess that it has taken a large amount of your drive up.

---

### Post by Elfy on 2008-06-29
That is beyond my ken I'm afraid - if you do end up going through and deleting things without getting any problems you will want to clean out your apt cache as it will be rather big I think.

```
sudo apt-get clean
```

will do that for you, but if you do start getting odd things occurring I would be inclined to do a reinstall. You'll be able to use your original partitions this time so won't need to do any partition work.

Good luck :D

---

### Post by Nothingpp on 2008-06-29
So euhm, how'd i uninstall ubuntu to reinstall it again? or do i just isnert the cd at start up?

---

### Post by Nothingpp on 2008-06-29
Ok Ubuntu's running a tad bit slow now but i can do everything again.
i used the recovery boot on start up ;d

---

### Post by Elfy on 2008-06-30
Reinstalling should be much simpler than the first install as you can use existing partitions.

Do as you did before - when it comes to the partitioning part of the process - choose manual.

You will get a new screen giving a visual representation of your partitions, one of them will be an ext3 partition - this should be your existing install.

Question - when you installed first tiem did you use one of the guided options? If you did then you should have only 1 ext3 partition, perhaps in an extended partition. If not and you have more than 1 ext3 partition and you are at all unsure ask the question - post the result of 

```
sudo fdisk -l
```

Back to the reinstall - 
1 - select the ext3 partition 
2 - click edit and you will get a new window
3 - at bottom right of new window - mountpoint button, click and choose / from dropdown menu
4 - exit that window
5 - select ext3 partition again and enable the format box

all done with that now and you can carry on - the install will now install to the original partition and reformat it

---

