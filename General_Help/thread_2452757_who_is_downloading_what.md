---
title: "who is downloading what?"
date: 2020-10-27
forum: General Help
---

### Post by jgw on 2020-10-27
I download stuff with sabnzbdplus and transmission.  However, that being said my machine shows that I have been downloading for a long time and I have no idea where its going or what is doing the downloading.  This is a mystery.  I tried taking a look with 'sudo ss -ntp' which gives a lot of info but nothing that tells me what is going on.

Thoughts?

---

### Post by crip720 on 2020-10-27
Transmission should tell if downloading or uploading, imagine the other one as well.  Should only download till file complete, depends on speed and seeds.  Nethogs will tell what program is using network, but not exactly if it is an extension in browser.  Some files might also contain the ability to download other related files if you don't pay enough attention, so instead of downloading one file you want, you also get to download other files (usually other files from uploader that might interest you).

---

### Post by jgw on 2020-10-28
thanks for the reply

As far as I could tell neither transmission OR sabnzbdplus had anything to do with whatever was being downloaded.  Firefox lists all downloads it does and it wasn't doing that either.  Its VERY mysterious!  I have no idea what it was.  I checked all my files to see which one was updated recently and there were none of any interest.  I know the downloading took place as I have my system monitor on which displays that kind of activity which is how I knew that there was downloading taking place.

---

### Post by DuckHook on 2020-10-28
For a real&#8209;time idea of what connections are being made through your network, try *iftop*.

Depending on your setup, it could be as simple as a system update. If this is paired with a slow mirror, then the update could take a long time. Like all such conjectures, mine is just a wild&#8209;eyed guess. It takes some detective work to nail such questions down and sometimes, there is no clear answer.

What do your logs tell you?

---

### Post by ActionParsnip on 2020-10-28
Transmission will tell you where the files are per torrent. You set this when you start the download. I believe the default is ~/Downloads

---

### Post by jgw on 2020-10-29
thanks for the reply.  I will give iftop a try next time.

the logs really didn't tell me much.  Well, maybe, it got a little too technical and I was not sure what I was looking at.  \\Thanks again!

---

