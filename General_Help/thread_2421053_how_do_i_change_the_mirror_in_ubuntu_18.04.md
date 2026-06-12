---
title: "how do i change the mirror in ubuntu 18.04"
date: 2019-06-15
forum: General Help
---

### Post by cluflynns on 2019-06-15
hello guys this is my first time on here but i was looking at a article on how to speed up ubuntu and i came across one tip which says to change your mirror to a closer one so your updates become faster below is a link to the article, the tip is in number 9.can anyone help me find this option

[https://ubuntuforums.org/showthread.php?t=2421053&p=13866460#post13866460](https://ubuntuforums.org/showthread.php?t=2421053&p=13866460#post13866460)

---

### Post by oldos2er on 2019-06-15
Your link does nothing but load your post here. 

Why is this thread marked 'Solved'? If it is indeed solved, please post the solution so that others may benefit from your experience.

---

### Post by #&amp;thj^% on 2019-06-15
100% agree with oldos2er with providing a solution.
If others want to try another method then:
Choosing the fastest mirror with "netselect" >>[https://pkgs.org/download/netselect-apt](https://pkgs.org/download/netselect-apt)
This solution is my preferred, as it guarantees the fastest mirror selection. For this we are going to use netselect command. The netselect package is not available within Ubuntu's standard repository by default, so we will need to borrow it from Debian stable repository:
```

sudo apt install wget
wget http://ftp.au.debian.org/debian/pool/main/n/netselect/netselect_0.3.ds1-26_amd64.deb
sudo dpkg -i netselect_0.3.ds1-28_amd64.deb
```
You may need to double check the version.
Once you have the netselect command available on your Ubuntu system use it to locate the fastest mirror based on the lowest icmp latency. The netselect output will be relative to your location. The below example output will show top 20 apt Ubuntu mirrors ( if available ):
```

sudo netselect -s 20 -t 40 $(wget -qO - mirrors.ubuntu.com/mirrors.txt)
   12 http://ubuntu.uberglobalmirror.com/archive/
   20 http://ubuntu.mirror.serversaustralia.com.au/ubuntu/
   21 http://ubuntu.mirror.digitalpacific.com.au/archive/
   38 http://mirror.aarnet.edu.au/pub/ubuntu/archive/
   39 http://mirror.overthewire.com.au/ubuntu/
   45 http://mirror.internode.on.net/pub/ubuntu/ubuntu/
  121 http://mirror.netspace.net.au/pub/ubuntu/
  148 http://mirror.waia.asn.au/ubuntu/
  152 http://mirror.as24220.net/pub/ubuntu-archive/
  162 http://mirror.tcc.wa.edu.au/ubuntu/
  664 http://archive.ubuntu.com/ubuntu/
  664 http://archive.ubuntu.com/ubuntu/
 3825 http://archive.ubuntu.com/ubuntu/
Only found 13 hosts out of 20 requested.
```

Alter manually your /etc/apt/sources.list file to reflect the above netselect results or use sed command, where the lower score number on the left represents a higher mirror transfer rate. 
Example only:
```

sudo sed -i 's/http:\/\/us.archive.ubuntu.com\/ubuntu\//http:\/\/ubuntu.uberglobalmirror.com\/archive\//' /etc/apt/sources.list
```

Comparing results
The following are my apt update command results, while located within the US:
```

US MIRROR ( http://us.archive.ubuntu.com/ubuntu ):
Fetched 23.1 MB in 20s (1148 kB/s) 

MIRROR protocol( mirror://mirrors.ubuntu.com/mirrors.txt):
Fetched 23.1 MB in 4min 45s (81.0 kB/s)

AU MIRROR ( http://au.archive.ubuntu.com/ubuntu ):
Fetched 23.1 MB in 12s (1788 kB/s)

NETSTAT Auto-Selected ( [http://ubuntu.uberglobalmirror.com/archive](http://ubuntu.uberglobalmirror.com/archive) ):
Fetched 23.1 MB in 6s (3544 kB/s)

```

---

### Post by garvinrick4 on 2019-06-16
#Link to mirrors for Ubuntu
[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)
Scroll to USA

Choose large size and either up to date or 6 hours behind.
Write it down. 
I use mirror.enzu.com/ubuntu  Is quite fast downloading updates.

Open App "Software Sources" You will see the mirror you are using now.
Change to one you want to use by choosing "other" and will ask to reload say yes.

Open a Terminal
> sudo apt-get update; sudo apt-get upgrade
Done

---

