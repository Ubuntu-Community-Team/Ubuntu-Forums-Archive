---
title: "Installing programs"
date: 2006-12-09
forum: General Help
---

### Post by gatorbowls on 2006-12-09
Im not sure how you install programs with linux? When ever I download a program for linux I get stuck and dont know what to do...Can someone give me directions on what I do.

---

### Post by YinZen on 2006-12-09
Ok don't worry, i felt exactly the same when i first started using Linux. In ubuntu there is a tool called synaptic package manager (SPM) which you can find by clicking System>Administration>Synaptic Package Manager. This is a great tool for getting new apps and programs. Before you start to use it though you need to add extra repositories (sources - basically just an address  where lots of apps are stored, and that synaptic can access). Have you added the extra repositories yet? If not heres a great guide to doing it [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories).

I think that the method that you have been using before now (downloading the tar.gz packages directly from a website?) is complex for a beginner. I didn't get the hang of those for a while. Its all about sorting out dependencies and making sure that the app has everything it needs to run. If just one app thats needed by the program is missing it can really mess things up during the install. The easiest thing to do if you still want to download directly from a website is to stick to .deb or .rpm files. The .deb files are native to the debian system so all you have to do is click them and it will make sure the program works fine with all the dependencies it needs. RPM files are a little more complex (they were first introduced into the Red Hat dist a while back) and need to be installed from a terminal. To install a .rpm this is what you do.
You need a package named alien to convert the .rpm's to deb's. To install it (you need to add the extra repositories that i mentioned earlier for this to be successful) open a terminal and type:
```

apt-get update
sudo apt-get install alien

```
then use 'cd' to get to the directory where your .rpm file is and type:
```

sudo alien -i nameofpackadge.rpm

```
Obviously you replace 'nameofpackadge.rpm' with the real name of your rpm file.
Hope this helped :-D .
Jake

---

### Post by gatorbowls on 2006-12-09
Ok..but im trying to install flash 9..and it said i had to go to a command line and type in some words..or something simular to that..where exsactly can i find command line?

---

### Post by YinZen on 2006-12-09
Ok well the command line is found by going to Applications>Accessories>Terminal. The linux terminal is what everybody will be referring to by saying 'command line'. When you get it open, have a try at installing flash 9 and post what happens back here. Also, what version of ubuntu are you using right now? Dapper or Edgy?

---

### Post by gatorbowls on 2006-12-09
im useing Edgy Eft  It said "file not found" I sent you a private message.

---

### Post by OmniCloud on 2006-12-10
Please don't send a private message man! LOL..I need help too. Everytime I download an application like say (RealPlayer10) it says I don't have a program that automatically installs applications. So I try the command line thing and it says command not found? How do you freaking install programs! I can't even visit gametrailers.com because none of the videos work? No flash..no one-click installation...Yup..completely lost. The only thing I got to work was Amarok to play MP3 files and it was only because it was one of the automatic installations and it installed MP3 playback automatically...I'm using Ubuntu version 6.10

---

### Post by aysiu on 2006-12-10
To install Flash 9, follow these instructions:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

