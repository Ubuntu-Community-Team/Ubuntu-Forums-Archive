---
title: "errors trying to install ubuntu-desktop on 12.04.1 LTS server"
date: 2013-03-25
forum: General Help
---

### Post by Click44 on 2013-03-25
I am running 12.04.1 LTS server, and I am trying to install a GUI (any will do - I mostly use the command line, but occationally a GUI is useful).

I did:

apt-get update
apt-get install ubuntu-desktop

I get the following error:
E: Unable to locate package ubuntu-desktop

apt and internet access ARE working (IE: I can run "apt-get update" and "apt-get upgrade")

I am using the default /etc/apt/source.list, and I believe that "main restricted", "precise universe", "precise multiverse", etc are all enabled.

Any help would be greatly appreciated.

---

### Post by ibjsb4 on 2013-03-25
IMO, you got lucky.  The ubuntu-desktop is a mega package.  For occasional use do you really want a full blown desktop?

Some other ideas here:

[URL="http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9"]http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=server+gui&sa=Search&cof=FORID:9

[http://packages.ubuntu.com/precise/ubuntu-desktop](http://packages.ubuntu.com/precise/ubuntu-desktop)
[/URL]

---

### Post by Click44 on 2013-03-25
Thanks, I tried some of those google links, no luck there either. For example, trying to install xorg:

apt-get install xorg
E: Package 'xorg' has no installation candidate

I don't really care if ubuntu-desktop is a "mega" package - I have plenty of disk space, I'm only installing on one server, and I'm planning on disabling the gui when I don't need it (IE: use "startx").

---

### Post by jnguyen on 2013-03-25
I found the best is install kubuntu-desktop because unity is too heavy for a server. I installed on all the servers here because every applications we use here required a GUI to install.
just my 2 cents.
jn

---

### Post by Click44 on 2013-03-25
[**[COLOR=#000000]jnguyen[/COLOR]**]("http://ubuntuforums.org/member.php?u=1037825") - thanks, kubuntu-desktop would work for me. Can you let me know the steps you use to install that?

---

### Post by ibjsb4 on 2013-03-25
Ok, something strange going on here.

Just to be sure, would you post your sources list.

```
cat /etc/apt/source.list
```

Your "sudo apt-get update" shows no errors?

---

### Post by Click44 on 2013-03-25
Sorry, apparently i DID have an issue in general with "apt-get update" and "apt-get install ubuntu-desktop"... some (but not all) stuff was being blocked by a firewall. I was able to get around the problem by having my network admin make the appropriate changes & all is working now. 

Thanks again for all your help.

---

### Post by ibjsb4 on 2013-03-25
That would do it :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

