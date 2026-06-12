---
title: "Updating get-iplayer to 2.82"
date: 2013-02-09
forum: General Help
---

### Post by grey1beard on 2013-02-09
I'm currently running 12.04 LTS, so do I need to remove version 2.80 of get-iplayer(or 2.78 on my wife's laptop) before I try to download the "ppa:jon-hedgerows/get-iplayer" for the 2.82 version ?

I've found this version often referred to as a solution to recent problems, but no mention of removal of earlier versions, except one, where ppa-purge comand was used.
Does this revert all ppa's installed, as I've no idea how to find what ppa's I have got, nor what the result of "using a sledgehammer to crack a walnut" might be ?

Advice and instruction gratefully received.
John

---

### Post by nothingspecial on 2013-02-09
If you add the ppa, you can just upgrade

```
sudo apt-get update && sudo apt-get upgrade
```

That's kind of the point of apt and ppa's and stuff.

You need to remove old versions when you compile a newer version of something.

---

### Post by grey1beard on 2013-02-09
Thanks nothingspecial - all done and dusted.

Perhaps the traditional advice to "measure twice, cut once" might be chaged to "read twice, and type once"
If I'd twice read the page I quoted in my op, I might have understood it a little better !

Regards
John

---

### Post by grey1beard on 2013-02-10
Perhaps, as usual, I was a bit quick off the mark.
I've managed to update my laptop to 2.82 OK, but my wife's, also running 12.04, doesn't upgrade.
I ran sudo apt-get update, then the following - 

> pippa@pippa-laptop:~$ sudo add-apt-repository ppa:jon-hedgerows/get-iplayer
[sudo] password for pippa: 
You are about to add the following PPA to your system:
 get-iplayer
 get_iplayer lists, searches and records BBC iPlayer TV/Radio, BBC Podcast programmes.
.......etc

then, after hitting the enter key as requested, got - 
> 
Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.7/threading.py", line 552, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 98, in run
    self.add_ppa_signing_key(self.ppa_path)
  File "/usr/lib/python2.7/dist-packages/softwareproperties/ppa.py", line 131, in add_ppa_signing_key
    tmp_keyring_dir = tempfile.mkdtemp()
  File "/usr/lib/python2.7/tempfile.py", line 315, in mkdtemp
    name = names.next()
  File "/usr/lib/python2.7/tempfile.py", line 134, in next
    letters = [choose(c) for dummy in "123456"]
  File "/usr/lib/python2.7/random.py", line 274, in choice
    return seq[int(self.random() * len(seq))]  # raises IndexError if seq is empty
ValueError: cannot convert float NaN to integer


"What to do now ?" you hear me cry. I don't speak techno.:-|

John

---

### Post by grey1beard on 2013-02-10
I've also jusy tried getting it via the Ubuntu software center, but that has produced the same result in terminal. :(

I've just gone back to the software centre on her laptop, and find that 2.79-2 is installed.
I'm still wondering if I'd be better off removing that first.
As it doesn't work, I can't see I've anything to lose !!

John

---

### Post by grey1beard on 2013-02-10
Have removed the 2.79-2 version, then used terminal and entered sudo apt-get update (this may not have been necessary), then went back to the software centre, and it offered 2.82-18-g1864c37-ppa8~oneiric.
Unfortunately, it then threw up an a window - "Package dependencies cannot be resolved"
The details just say > "The following packages have unmet dependencies :
get-iplayer

so I guess I have to get something, but not sure what or how :(

---

### Post by scouser73 on 2013-02-10
> **grey1beard said:**
> Have removed the 2.79-2 version, then used terminal and entered sudo apt-get update (this may not have been necessary), then went back to the software centre, and it offered 2.82-18-g1864c37-ppa8~oneiric.
Unfortunately, it then threw up an a window - "Package dependencies cannot be resolved"
The details just say 

so I guess I have to get something, but not sure what or how :(

```
sudo apt-get autoremove get-iplayer
```

Then go to the Home folder, press **Ctrl & H**, and if it's there then delete the **.get_iplayer** folder.

---

### Post by grey1beard on 2013-02-10
More info

Exploring her laptop Home folder, I discover a get_iplayer-2.78 folder (please note underscore), with a date Jan 2011, probably when I first installed it, but also a .get_iplayer folder, dated yesterday, when we were trying, and failing to download Borgen from the BBC.

My use of the software centre this morning to remove 2.78 seems to have had no effect on these folders.
I'm left wondering if I should try renaming them (old-...) and trying again, or will there be something else in my file system that will trip up the attempt ?

---

### Post by grey1beard on 2013-02-10
Hi scouser, missed your post.
I'll give that a go now.
John

---

### Post by grey1beard on 2013-02-10
Responce was " get-iplayer not installed, so not removed"
OK, I'll do the same with get_iplayer.
Fingers crossed. ;)

---

### Post by grey1beard on 2013-02-10
Nope.
I've tried autoremove on get-iplayer, get_iplayer, get_iplayer-2.78, and .get_iplayer.
All to no avail. I've used the folder names as shown on the Home directory list view.

John

---

### Post by scouser73 on 2013-02-10
Hi John,

[http://ftp.ie.debian.org/debian/pool/main/g/get-iplayer/get-iplayer_2.82-2_all.deb](http://ftp.ie.debian.org/debian/pool/main/g/get-iplayer/get-iplayer_2.82-2_all.deb)

Hope this helps. ;)

Denis.

---

### Post by grey1beard on 2013-02-10
Hi Dennis,
All started OK, but it kept failing to download the packages, and asked me to check my internet connections.
As they are 100% at the moment, I tried for a third time via terminal, and it spelled out the source of the problem.
The story so far -

> pippa@pippa-laptop:~/Desktop$ sudo dpkg -i get-iplayer_2.82-2_all.deb
[sudo] password for pippa: 
Selecting previously deselected package get-iplayer.
(Reading database ... 238865 files and directories currently installed.)
Unpacking get-iplayer (from get-iplayer_2.82-2_all.deb) ...
dpkg: dependency problems prevent configuration of get-iplayer:
 get-iplayer depends on rtmpdump | flvstreamer; however:
  Package rtmpdump is not installed.
  Package flvstreamer is not installed.
 get-iplayer depends on libxml-simple-perl; however:
  Package libxml-simple-perl is not installed.
dpkg: error processing get-iplayer (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db ...
Errors were encountered while processing:
 get-iplayer


so I assume I need to *apt-get install* rtmdump, flvstreamer and libxml-simple-perl, then run dpkg again ?
John

---

### Post by grey1beard on 2013-02-10
I have run apt-get install on packages rtmdump, flvstreamer and libxml-simple-perl, then run dpkg again.
I then ran sudo apt-get update, and tried get-iplayer once more.
Although it now lists 2.82 as the current package, it still doesn't download.
It gives me the correct available downloads etc., but when I try to run get-iplayer -g to save the download, it gives me the same error messages we were getting before.

John
EDIT
> Error: Last tag size must be greater/equal zero(prev tagsize=-1218841788)and smaller than filesize, corrupt file!

---

### Post by scouser73 on 2013-02-10
Fix any broken packages with this command;

```
sudo apt-get install -f
```

Copy and paste the following into Terminal
```
get_iplayer --force it --pid 
```

Then copy and paste the programme link you want get-iplayer to download, so for example Eastenders would be the following;

get_iplayer --force it --pid [http://www.bbc.co.uk/iplayer/episode/b01qqwd3/EastEnders_Omnibus_10_02_2013/](http://www.bbc.co.uk/iplayer/episode/b01qqwd3/EastEnders_Omnibus_10_02_2013/)

I've chosen to use the **--force it** command in this instance, as this will work on a programme that you've previously started to download but the get-iplayer cache won't allow for a second download unless the command is used.

[COLOR="Red"]***There needs to be a space after [B]--pid** part of the command*[/B][/COLOR]

---

### Post by grey1beard on 2013-02-10
Hi Dennis,
I've just set that going on the other laptop, but I'm getting the identical error message !

John

---

### Post by scouser73 on 2013-02-10
> **grey1beard said:**
> Hi Dennis,
I've just set that going on the other laptop, but I'm getting the identical error message !

John

Okay, in Terminal enter ```
sudo nautilus
``` and enter your password then make your way to **USR > Share ** & delete the **get_iplayer** folder and check if that's fixed it.

---

### Post by grey1beard on 2013-02-10
Tried again after following you instruction, and it 
> 
INFO: Connected ...

As the signal was only 75% where I was located, I transferred to another room to be closer to my router.
Termainal then produced the line

> WARNING: HandleInvoke, Sanity failed. no string method in invoke packet
and is currently static.

No, it has just started and is currently downloading.

I'll confirm when it manages to complete.
John

---

### Post by grey1beard on 2013-02-10
Hi Dennis,
Thanks for your help in steering me through to a successfull result.
After the line I posted above, terminal threw up - 
> INFO: Connected...
WARNING: HandleInvoke, Sanity failed. no string method in invoke packet
ERROR: RTMP_ReadPacket, failed to read RTMP packet body. len: 12563141
INFO: Command exit code 1 (raw code = 256)
WARNING: Failed to stream file /home/pippa/Blandings_-_4._The_Crime_Wave_at_Blandings_b01qm822_default.partial.mp4.flv via RTMP
INFO: skipping flashhigh1 mode
INFO: Trying flashhigh2 mode to record tv: Blandings - 4. The Crime Wave at Blandings
INFO: File name prefix = Blandings_-_4._The_Crime_Wave_at_Blandings_b01qm822_default                 
RTMPDump v2.4-n37-git4e06e21-ppa6~oneiric
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
INFO: Connected...

and then ran perfectly.

Two things. I notice in the code that it finally ran the *flashhigh2 mode* OK, but have no idea till I use google of the significance of this, but more usefully to me - is it possible for me to just use the pid number, which I see appearing when I do an initial search for the programme I'm looking for, when I type *get-iplayer "keyword for programme"* into terminal ?
Regards and thanks,
John

---

### Post by scouser73 on 2013-02-10
> **grey1beard said:**
> Hi Dennis,
Thanks for your help in steering me through to a successfull result.
After the line I posted above, terminal threw up - 


and then ran perfectly.

Two things. I notice in the code that it finally ran the *flashhigh2 mode* OK, but have no idea till I use google of the significance of this, but more usefully to me - is it possible for me to just use the pid number, which I see appearing when I do an initial search for the programme I'm looking for, when I type *get-iplayer "keyword for programme"* into terminal ?
Regards and thanks,
John

Yeah, you can just use the pid number rather than the whole url, which I came across today when I was searching for a solution to the problem.

I don't know whether you have anything similar but I have a list of commands for programmes, from standard definition to high definition if you'd like them.

**_Get iPlayer Codes_**

get_iplayer --pid

get_iplayer --type=tv --pid= --modes=flashstd

get_iplayer --type=tv --pid= --modes=flashhigh

get_iplayer --type=tv --pid= --modes=flashhd

get_iplayer --force it --pid

get_iplayer --force it --pid --modes=flashhd

Anyway, glad you got it sorted.

Denis.

---

### Post by grey1beard on 2013-02-10
Thanks for those codes Dennis. I think we probably only need the standard download as we've never used HD.

Originally, and I shall be trying this again, we only used the number that appears at the begining of the line after we run the initial search - *get-iplayer -g xxx* sort of thing. Very easy for us oldies.

Hope the weather is better in Liverpool than it is here in stormy Norfolk.
Regards
John

---

