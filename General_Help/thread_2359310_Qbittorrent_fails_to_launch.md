---
title: "Qbittorrent fails to launch"
date: 2017-04-22
forum: General Help
---

### Post by johnstefnds on 2017-04-22
First I need to say that Qbittorrent used to work fine... on this PC and version of ubuntu. 

I also need to say (although I dont know if its related or just a coincidence) that the program started to pop an error when trying to load it after I once tried to load it via the terminal in sudo mode $ sudo qbittorrent 


An error window pops with more details but I dont know how to copy it here and it has way more details that a single screen-shot could contain so I could maybe answer some questions or if you know any other way to gather more intel on the specific error I will do so upon your instructions. 

While trying to launch qbittorrent never works (either by console or when clicking the icon ) $sudo qbittorrent still works fine without issues. 

I tried to remove/purge qbittorrent and reinstall it but nothing had changed. 


my kernel version is 4.8.0-46-generic and my ubuntu version is 16.10

---

### Post by monkeybrain20122 on 2017-04-22
Maybe some of your settings are messed up. Close qbittorrent. Open the file manager, press ctrl +h to show hidden folders (or from dropdown) , then open the folder .config and delete the subfolder qBittorrent. Then start qbittorrent.

P.S. Is there any reason that you start qbittorrent with sudo? I don't think it is a good idea.

---

### Post by johnstefnds on 2017-04-23
Currently I am downloading something so I will try this in a few thanks though I post the results later.

I wouldnt care about "sudoing" the app its just that for some reason it doesnt save files to a secondary internal disk in my computer (which doesnt have any OS on it its use is just to save files videos etc) but when I used sudo qbittorrent then it could save those files although after the first time I did that then the "normal" qbittorrent wouldnt open as I described above. 

EDIT: nope nothing happened...

After I did what you said I restarted the computer and I tried to launch it by doubleclicking the qb icon a legal notice window appeared but nothing after that ....

---

### Post by rburkartjo on 2017-04-23
try reinstalling it
[https://pkgs.org/download/qbittorrent](https://pkgs.org/download/qbittorrent)

---

### Post by johnstefnds on 2017-04-24
I did reinstall it but it didnt fix the issue

---

### Post by monkeybrain20122 on 2017-04-24
Has it ever worked? Seems that an up to date version of qbittorrent failed to build in 16.10. [https://launchpad.net/~qbittorrent-team/+archive/ubuntu/qbittorrent-stable?field.series_filter=yakkety](https://launchpad.net/~qbittorrent-team/+archive/ubuntu/qbittorrent-stable?field.series_filter=yakkety) Ubuntu releases likely ship with an old version but it might have other issues.

I am on 16.04 and upgraded to qbittorrent 3.3.12 with the ppa with no problem. It doesn't work with 16.10 and 17.04 at the moment (packages failed to build, see above) So I would add the ppa so when they build the package successfully you will get upgrade. Meanwhile if you can't fix the problem use different torrent client temporarily (transmission, deluge, to name two)

P.S It seems that the reason you need sudo to access the second partition has to do with the fact that you have no permission to enter that partition. To confirm that just try to view it with the file manager and see if it asks you for password. If that is the case instead of using sudo everytime when you try to access it just change its ownership to you with a command like

sudo chown yourusername /media/... 

where /media/... is the path to your external drive/partition. You can find it by opening it with the file manager and press ctrl+L, it will show up at the address bar (is that what it is called?)

---

### Post by monkeybrain20122 on 2017-04-24
BTW you can just start qbittorrent in the terminal and copy  and paste the error message.

---

### Post by johnstefnds on 2017-04-25
> **monkeybrain20122 said:**
> Has it ever worked? Seems that an up to date version of qbittorrent failed to build in 16.10. [https://launchpad.net/~qbittorrent-team/+archive/ubuntu/qbittorrent-stable?field.series_filter=yakkety](https://launchpad.net/~qbittorrent-team/+archive/ubuntu/qbittorrent-stable?field.series_filter=yakkety) Ubuntu releases likely ship with an old version but it might have other issues.

I am on 16.04 and upgraded to qbittorrent 3.3.12 with the ppa with no problem. It doesn't work with 16.10 and 17.04 at the moment (packages failed to build, see above) So I would add the ppa so when they build the package successfully you will get upgrade. Meanwhile if you can't fix the problem use different torrent client temporarily (transmission, deluge, to name two)

P.S It seems that the reason you need sudo to access the second partition has to do with the fact that you have no permission to enter that partition. To confirm that just try to view it with the file manager and see if it asks you for password. If that is the case instead of using sudo everytime when you try to access it just change its ownership to you with a command like

sudo chown yourusername /media/... 

where /media/... is the path to your external drive/partition. You can find it by opening it with the file manager and press ctrl+L, it will show up at the address bar (is that what it is called?)


Yes it did work fine on 16.10 I only had to set manually (by googling ) on how to make it the default app to open magnet links. 

It only started not working after I tried to run it as sudo (but when I try to run it as sudo now it still works fine) and I had no issues installing the package I downloaded from their site.


> **monkeybrain20122 said:**
> BTW you can just start qbittorrent in  the terminal and copy  and paste the error message.

You just blew my mind! :P How didnt I thought of that! :P

Here is the output of the terminal when trying to run qbittorrent without the sudo prefix:

```
terminate called after throwing an instance of 'std::runtime_error'
 [COLOR=#ff0000] what():  Cannot write to torrent resume folder.[/COLOR]


*************************************************************
Catching signal: SIGABRT
Please file a bug report at http://bug.qbittorrent.org and provide the following information:

qBittorrent version: v3.3.7
stack trace:
  /lib/x86_64-linux-gnu/libc.so.6 : gsignal()+0x9f  [0x7f2f77c247ef]
  /lib/x86_64-linux-gnu/libc.so.6 : abort()+0x16a  [0x7f2f77c263ea]
  /usr/lib/x86_64-linux-gnu/libstdc++.so.6 : __gnu_cxx::__verbose_terminate_handler()+0x16d  [0x7f2f7857058d]
  /usr/lib/x86_64-linux-gnu/libstdc++.so.6 : ()+0x8f336  [0x7f2f7856e336]
  /usr/lib/x86_64-linux-gnu/libstdc++.so.6 : ()+0x8f381  [0x7f2f7856e381]
  /usr/lib/x86_64-linux-gnu/libstdc++.so.6 : ()+0x8f599  [0x7f2f7856e599]
  qbittorrent : BitTorrent::Session::initResumeFolder()+0x20e  [0x55a888da38ae]
  qbittorrent : BitTorrent::Session::Session(QObject*)+0x214  [0x55a888da8014]
  qbittorrent : BitTorrent::Session::initInstance()+0x37  [0x55a888da9167]
  qbittorrent : Application::exec(QStringList const&)+0x36  [0x55a888d406c6]
  qbittorrent : main()+0x490  [0x55a888d36a60]
  /lib/x86_64-linux-gnu/libc.so.6 : __libc_start_main()+0xf1  [0x7f2f77c0f3f1]
  qbittorrent : _start()+0x2a  [0x55a888d3aeea]
Aborted (core dumped)


```

Again  though if open the terminal and run qbittorrent WITH the sudo prefix  everything works fine (I have to copy/paste manually the magnet links  though )

P.S is the line colored as red related to the issue I mentioned in my OP? I mean could it be that for some reason it cant access the directory of the files which in the past it used to download and save but now for some reason doesnt have permission to do that? 

How could I investigate further into something like that?

---

### Post by johnstefnds on 2017-04-27
still nothing :(

---

