---
title: "MOZILLA_FIVE_HOME declaration not being respected"
date: 2008-04-23
forum: General Help
---

### Post by dehuszar on 2008-04-23
I am setting up the Lotus Notes client 8.0.1 for Linux on Hardy Heron.  

Lotus Notes 8.0.1 doesn't like newer xulrunner versions, and so in Gutsy I had to set up xulrunner 1.8.0.4 in /opt/xulrunner, put a MOZILLA_FIVE_HOME statement in the launch script for Notes, put a GRE definition (called 1.8.conf) in /etc/gre.d/ and everything worked fine.

In Hardy, things no longer work fine.  The same configuration seems to insist on using Firefox 3's GRE definition no matter where I try and define MOZILLA_FIVE_HOME, be it in the /etc/profile or ~/.bashrc files, it still uses the 1.9b5 GRE definition causing rendering issues in Notes.

I've poured through countless related Eclipse/Aptana articles which have similar xulrunner embedding issues.

Does anyone know another way I can make my version the one that displays when I type xulrunner -v from the command prompt?  If I do it anywhere other than /opt/xulrunner I get "1.9b5 - 2008041514" as my answer.  I think until I can get the response to be 1.8.0.4 I will continue to experience these issues.  Adding /opt/xulrunner to the $PATH and $LD_LIBRARY_PATH statements seem not to matter, and I don't see any sign of firefox, mozilla, or xulrunner in either statement.  :(

Any help would be greatly appreciated.

Thanks in advance,
Sam

---

### Post by dehuszar on 2008-04-28
Anyone?  Bueller?

---

### Post by Blues- on 2008-05-05
This is how I got html messages in Notes 8.01 working in hardy, 
nb, I'm using Firefox2, but this should work for both versions.

1) d/l xulrunner 1.8.0.4 into your /opt directory and untar
```

cd /opt/
sudo wget http://ftp.mozilla.org/pub/mozilla.org/xulrunner/releases/1.8.0.4/linux-i686/en-US/xulrunner-1.8.0.4.en-US.linux-i686.tar.gz
sudo tar -xzf xulrunner-1.8.0.4.en-US.linux-i686.tar.gz

```

2) Update the gre.d configuration to use the 1.8 xulrunner
```

cd /etc/gre.d/
sudo touch 1.8.conf
sudo nano 1.8.conf

```

3) Add the following lines to the file.
(use crtl-insert to paste in nano and ctrl-x to exit and save)
```

[1.8.0.4]
GRE_PATH=/opt/xulrunner
xulrunner=true

```

4) Export new MOZILLA_FIVE_HOME path
```

export MOZILLA_FIVE_HOME=/opt/xulrunner

```

Launch Notes and read your html messages :)

You can also create a launcher so you don't need to export the MOZILLA..
variable each time, before you start notes ..
```

--------start notes8.sh---------
#!/bin/bash
export MOZILLA_FIVE_HOME=/opt/xulrunner
/opt/ibm/lotus/notes/notes
--------end of notes8.sh--------

```


Optional steps that could be needed, but everything worked fine for me without them ..

Register the XULRunner to the system
```

Register XULRunner with the system by running xulrunner --register-global (to install for all users, must be run as root) or xulrunner --register-user (to install for one user only).

```


Hope this helps and works for you :)
Cheers,
Blues-.

---

### Post by dehuszar on 2008-05-06
Hey,

  Thanks for your response.  That said, if you read my post, you will see that this is exactly what I already did, and stated that it worked in Gutsy, which I'm guessing you are using since you mention Firefox 2.  In Hardy Heron (8.04) where Firefox 3.0b is the default, this method no longer works.  

  No matter what order the .conf files are ordered in, the export statement specifying the xulrunner version that I place in my /etc/profile document, .bashrc, or Notes start script doesn't actually set that preference for the program.

  That's what I'm trying to wrestle with, currently.

---

### Post by Blues- on 2008-05-06
Take a look at this approach ...
=> [http://janochrastina.blogspot.com/2008/03/lotus-notes-801-on-ubuntu-710.html](http://janochrastina.blogspot.com/2008/03/lotus-notes-801-on-ubuntu-710.html)


Editing the lotus/notes/data/workspace/.config/rcpinstall.properties could work.

---

### Post by dehuszar on 2008-05-26
On it's face, it does not.  There may be some other tweak required to make it go, but thus far, it appears to be an issue of the required version simply not being respected when there is another, newer version that the system can detect.

Not sure how to proceed from here.

---

### Post by dehuszar on 2008-06-10
Well it looks like the 8.5 beta does the trick!  Everything works out of the box (knock on wood)!  Now on to Widgets & Live Text

---

