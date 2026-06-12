---
title: "adept manager can't access database"
date: 2007-02-02
forum: General Help
---

### Post by agentsmith270288 on 2007-02-02
i tried to install extra codecs for multimedia play back and i must have entered a wrong repository and now apt manager has a problem accessing updates database. How do I solve this problem?

---

### Post by jasutton on 2007-02-02
What does the error report?

Also, what does your /etc/apt/sources.list look like?

---

### Post by agentsmith270288 on 2007-02-02
error report says that apt manager cannot get updates and then suggests that i run apt-get update or apt setup through terminal. i've added a wrong repository and it causes the problem. i cant get rid of it because adept manager quits after i close the error popup. i tried to manually delete that particular directory using kate editor but it keeps saying i have no privileges to do that. i need to get rid of the first line libxine-extracodecs:

libxine-extracodecs

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted 

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted 
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe multiverse 
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe multiverse 

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse 
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted 
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse 
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse

---

### Post by tylerdurdendb on 2007-02-23
Hello,

My first post here but I had to comment on this one.

I had the exact same error that you had agentsmith270288 and my source.list file looked the exact same as yours.  I think we must have been trying those codecs the same way. :) But I just wanted to mention that I was able to fix the issue by right clicking on the file source.list file and choosing actions> edit as root. I was then able to remove the offending entry and save the new source.list file.  Being a noob from one of those 'other' operating systems and not knowing totally what I was doing I also rebooted, not sure it that was needed but I did it.  

This fixed the issue for me but I just wanted to mention again that I am really new at this and the whole reason I did it that way is that I am still not all that comfortable with command line stuff just yet.  So if there is someone out there more knowledgeable then I that knows this to be a really bad idea in doing it this way please let me know!

Thanks

---

