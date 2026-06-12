---
title: "hellanzb sends as much data as it recieves since hardy beta's"
date: 2008-04-26
forum: General Help
---

### Post by Roderik on 2008-04-26
I've been using hellanzb for years, as i've been using ubuntu, but the last few weeks i'm running into some strange problem. Downloading a nzb will not run over 15kb/s while downloading from http/ftp runs at 400kb/s

So this is what i ruled out:

1. the newsserver from my isp would over time sometimes work badly, so i renewed my eweka.nl payed server account, no improvement.
2. I installed hardy final yesterday, did apt-get install hellanzb and redid the entire config file. (added server and changed the path's to my download disk, see attachment)
3. Checked my router and disabled QOS. Noticed it was sending as much kb/s as it recieves (what would explain the speed problem since i'm on adsl), why i'm not sure. Verified the router data with iptraf.
4. Installed a newsgroup leech program on my windows laptop, used the same nzb file -> 400+ kb/s (behind the same router, using the same newsserver)

so now i'm confused as to what the problem can be, and how i can solve it... The only thing i didn't try was using another newsleech program on hardy, because i don't know any :)

---

### Post by Roderik on 2008-04-26
for those interested, i also posted a bugreport: [https://bugs.launchpad.net/ubuntu/+source/hellanzb/+bug/222617](https://bugs.launchpad.net/ubuntu/+source/hellanzb/+bug/222617)

---

### Post by kebes on 2008-06-10
I ran into what sounds like the same bug after installing Hellanzb on Kubuntu 8.04 (Hardy Heron) (similar to [this]("https://bugs.launchpad.net/ubuntu/+source/hellanzb/+bug/222617") and [this]("https://bugs.launchpad.net/ubuntu/+source/hellanzb/+bug/233900") bug report).

The problem was basically that the reported download speed was very low (1/10th the speed it should be), and that Hellanzb was uploading as much as it was downloading. Moreover, the debug log (which can be found at ~/.hellanzb/log-debug if you've activated it) had repeated error messages like:
```

2008-06-09 20:47:27,625 giganews[6] getting GROUP:  alt.binaries.t
2008-06-09 20:47:27,625 giganews[8] got GROUP: alt.binaries.t
2008-06-09 20:47:27,626 giganews[8] getting GROUP:  alt.binaries.t
2008-06-09 20:47:27,627 giganews[2] got GROUP: alt.binaries.t
2008-06-09 20:47:27,627 giganews[2] getting GROUP:  alt.binaries.t
2008-06-09 20:47:27,629 giganews[9] got GROUP: alt.binaries.t
2008-06-09 20:47:27,629 giganews[9] getting GROUP:  alt.binaries.t
2008-06-09 20:47:27,631 giganews[4] got GROUP: alt.binaries.t
2008-06-09 20:47:27,631 giganews[4] getting GROUP:  alt.binaries.t
2008-06-09 20:47:27,636 giganews[3] got GROUP: alt.binaries.t

```
Basically Hellanzb is repeatedly trying to resolve a newsgroup, but is failing.


The solution (at least for my problem) is described in [this bug report]("http://www.hellanzb.com/trac/hellanzb/ticket/393#comment:6"). Basically there is a bug in the file:
```
/usr/share/python-support/hellanzb/Hellanzb/NZBLeecher/Protocol.py
```
where it is not cleaning the "groups" string properly. To fix it, edit that file, and below line 513, add a single line of python code that simply does "group = group.strip()". So:
```
$ sudo nano /usr/share/python-support/hellanzb/Hellanzb/NZBLeecher/Protocol.py
```
Then find the code near line 513 and change it like so:
```

       if not self.factory.skipGroupCmd:
            # Change group
            for group in self.currentSegment.nzbFile.groups:
[B]
[COLOR="Red"]                # Added to fix bug
                group = group.strip()
[/COLOR][/B]
                # NOTE: we could get away with activating only one of the groups instead
                # of all
                if group not in self.activeGroups and group not in self.failedGroups:
                    debug(str(self) + ' getting GROUP: ' + group)
                    self.fetchGroup(group)
                    return


```


The above fix worked perfectly for me. Hope that helps someone else.

---

### Post by Bodai on 2008-06-22
That is very helpful. Thanks for sharing. I have 2 active installations of hellanzb and only 1 of them started 2 weeks ago to have problems with down rate. For me the rate went from 900Kbs => 1 Kbs => 900Kbs.

---

### Post by Roderik on 2008-06-22
I changed from hellanzb to [http://www.sabnzbd.org/](http://www.sabnzbd.org/), also a free platform independant python script for automatic downloading. the reason i don't change back with thee sollutions, is that i love the rss download feature.

---

### Post by Skerit on 2008-09-14
This fix works great on Hardy but it crashes hellanzb on intrepid.

Edit: strangely enough typing in the code didn't work, but copying and pasting it did. Go figure
Edit2: This was before I knew python syntax, I had too many enters ;)

---

### Post by RaZoR1394 on 2008-12-22
Hellanzb has worked fairly well for me, unfortunately there are bugs that sometimes interrupt seriously.

I'm using this now

[http://forums.sabnzbd.org/index.php?topic=387.0](http://forums.sabnzbd.org/index.php?topic=387.0)

---

