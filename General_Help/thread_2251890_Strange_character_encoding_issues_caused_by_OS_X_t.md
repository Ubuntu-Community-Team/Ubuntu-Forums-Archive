---
title: "Strange character encoding issues caused by OS X to Ubuntu rsyncing (NFD =&gt; NFC)"
date: 2014-11-07
forum: General Help
---

### Post by User4519 on 2014-11-07
Hi :)

I've been using a Mac as my primary laptop for quite a bit now, and I do a lot of file transfers from that Mac to my server, which is running Ubuntu.

I prefer doing this with rsync as I then don't have to mount shares, it's faster, and I can use checksummed copying.

Today I started noticing some strangeness with an NFS export on my server that I set up and mounted on my laptop yesterday. Some debugging time later, I've now learned that OS X UTF-8 isn't the same as everyone else's, Linux included. The whole NFC vs NFD thing.

As for the NFS mount, adding "nfc" to the mount options fixes this, and I can properly read and write files on this share without issues. Characters are written and read correctly, an å is the same on both sides of the pond :)

The issue I'm having, though, is that since I had no idea that this difference existed, I have been rsyncing quite a lot of data (how much I really don't know) without using the iconv option to properly convert from NFD to NFC when transferring.

So, I'm having a currently unknown number of files and folders on my Ubuntu server that have "funky" special characters, such as ä, ö, and å. The funkiness here is that they actually look perfectly fine on the server when I connect to it by SSH (it's headless). I can do a directory listing, and see for instance:

```
drwxr-xr-x 2 daniel daniel  7   2014-07-24 19:16:48   Jungfrukällan 1960.mkv
```

On the NFS mount on the Mac side, however, the file doesn't show up at all in Finder, and in a shell listing of the NFS share I get:

```
?????????? ? ?       ?                    ? Jungfruka??llan 1960.mkv
```

And here's the kicker: The ä in this filename shows fine in my SSH sessions, but it's not the same ä that I can type in with my keyboard. If I do, for instance,

```
mv Jungfrukällan 1960.mkv Jungfrukällan 1960.mkv
```

Then it suddenly appears on the Mac side in Finder, and it also now lists healthily with attributes and ownership in a shell session there (except with '??' instead of the ä).

The notable thing about the mv command above is that I have to use tab completion to target the source file, and do that before typing in the ä, i.e.```
mv Jungfru<tab>
``` will complete, whereas ```
mv Jungfrukä<tab>
``` will not, because the ä I type in there is not the same as the ä that is listed by ls.

Or rather, ls does not actually list the character as it really is stored. Somewhere along the line the "sick" ä is being converted to a "sane" one. I cannot copy the ä from ls's output and paste it as part of a command and successfully target the file. Only tab completion will let me target it.

If it's SSH "cleaning up", if it's the terminal app, or if it's the shell I cannot tell. I can say that it happens with bash, zsh, and sh on the server, it happens with iTerm2 and Terminal on the Mac, and it happens with Konsole on Kubuntu. They all show the "sick" and "sane" ä chars exactly the same.

In XBMC, which runs locally on the server, I can, however see a "sick" ä as "a " and a sick ö as "o ", which looks like two bytes of a unicode sequence "spelled out".

I thought that since this problem was seemingly caused by my failing to do iconv when rsyncing I might be able to fix it with convmv. The man page states that "convmv is able to convert files from NFC to NFD or vice versa" but I cannot see how I would do that. --nfd and --nfc both apply to the target encoding.

The list of possible input encodings does not include the "utf-8-mac" one that rsync apparently does. There's only one type of utf-8, and the Mac* ones, e.g. MacCentralEurRoman or MacRoman don't do much. Whatever I choose, convmv tells me "Skipping, already UTF-8"... Which is true, it's just that it's not quite the UTF-8 kind I need.

I'm not quite sure how I can find and fix these files in a (semi-)automated manner. I can't copy the "sick" characters and search for them with find or locate as the characters presented to me in file listings have already been translated to sane ones...

Any ideas here?

Thank you :)

For reference:

Ubuntu 14.04
ZFS (ZFS on Linux)

locale:
```
LANG=en_US.UTF-8LANGUAGE=en_US:en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=en_US.UTF-8
```

---

### Post by User4519 on 2014-11-07
HAHAHA :D

Oh, how I love rubberducking! :D

I just finished that long long long post, and then I thought, "I wonder if it's safe to just force convmv to process **all** filenames and then maybe it'll turn those funky NFD files into NFC?"

Well, so I tried in a small folder with known bad filenames, and thought I'd better then remove the "from", i.e. -f switch, but convmv errored out... So I thought, well maybe I can just use "utf-8" for both the "from" and "to" switch, and then it dawned on me — **that's** how you do NFD to NFC conversion:

```
convmv -f utf8 -t utf8 --nfc -r .
```

And then, once I'd confirmed that all the renamings it'd like to perform were sound,

```
convmv -f utf8 -t utf8 --nfc -r --notest .
```

Perfect! It worked! And it **only** renamed those that actually had NFD-encoded special chars. It skipped right over NFC-encoded special chars. Beautiful!

I'm gonna run this on the entire server archive right now :)

So much for writing a useless post. Hopefully someone else will stumbe across it and it'll help them :)

YAYAYAYAAA!!! Have a nice weekend everyone! :)

---

