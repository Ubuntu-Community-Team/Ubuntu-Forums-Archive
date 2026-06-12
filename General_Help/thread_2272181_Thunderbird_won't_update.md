---
title: "Thunderbird won't update"
date: 2015-04-04
forum: General Help
---

### Post by ray9 on 2015-04-04
Ubuntu 14.04 LTS.  I see that Thunderbird 31.6 has been released.  Since I never was able to get 31.5 installed I thought that maybe I would have better luck with 31.6.  No.  Installed it through synaptic and everything went fine but T'Bird is still 31.4.  What am I doing wrong here?

---

### Post by deadflowr on 2015-04-04
I'm hoping you restarted thunderbird.
You can also double check the 31.6 version is installed with the terminal command
```
 apt-cache policy thunderbird
```
should output something like

```
thunderbird:
  Installed: 1:31.6.0+build1-0ubuntu1
  Candidate: 1:31.6.0+build1-0ubuntu1
  Version table:
 *** 1:31.6.0+build1-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ vivid/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by ray9 on 2015-04-05
Thank you for the reply.  With that command it says it's 31.6.  But when I click "About  Thunderbird" it shows 31.4.  And the T'Bird updater is still prompting me.  Since day one the T'bird updater keeps on saying "Connecting to the update server" like forever.

---

### Post by deadflowr on 2015-04-05
thunderbird updater?
that should be disabled in Ubuntu.
is this from mozilla directly?

Double take edit: you mean the thunderbird updater and not the email updater used in thunderbird, right?
At least that is what I think you mean.
Correct me if I'm wrong.

---

### Post by ray9 on 2015-04-05
I don't know, It's a window that opens up telling to to upgrade to the new T'Bird, says "hide" on the bottom left.  And just now I clicked on "about T'bird" and it still says 31.4 and to upgrade to the newer version.  Which takes me to Mozilla  to download a .tar file.

---

### Post by ray9 on 2015-04-18
I don't know how important it REALLY is to update but, can ANYBODY tell me why I can't update T'Bird?

---

### Post by deadflowr on 2015-04-18
Did you install t-bird from mozilla, or are you using the Ubuntu version?

---

### Post by ray9 on 2015-04-21
Ubuntu

---

### Post by matt_symes on 2015-04-21
Hi

Let's try to get to the bottom of this.

Open a terminal and copy and paste these commands into it. Copy and paste the results from the terminal into your next post. 

Don't just tell me what they say, i really need to see the actual output: so highlight the output in the terminal -> right click copy and paste into your next post.

```
dpkg -l thunderbird
```

```
whereis thunderbird
```

```
which thunderbird
```

```
/usr/bin/thunderbird --version
```

```
file /usr/bin/thunderbird
```

```
echo $PATH
```

If you start thunderbird from the terminal and go to the about screen, do you see version 3.14 or 3.16 ?

To do this, type this into the terminal

```
/usr/bin/thunderbird
```

Post back the results from those commands and then we can investigate the next part after.

Kind regards

---

