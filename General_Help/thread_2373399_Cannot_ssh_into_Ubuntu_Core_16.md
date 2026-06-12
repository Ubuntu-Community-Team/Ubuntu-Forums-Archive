---
title: "Cannot ssh into Ubuntu Core 16"
date: 2017-10-05
forum: General Help
---

### Post by BL86vYR on 2017-10-05
Sorry if this is a repeat question.

        I have a Nextcloud 11 snap running on Ubuntu Core 16 on a Raspberry Pi 2. I set it up via ssh without issue by uploading the public ssh key into Ubuntu One. It is still working perfectly as a Nextcloud box.

        I tried to ssh into the pi yesterday, and I was prompted for a password for [EMAIL="UbuntuSSO@192.168.X.XXX"]UbuntuSSO@192.168.X.XXX[/EMAIL], which is strange as I had never set up a password for the key.
        I realized that I may have reformatted my laptop without backing up the ssh keys, so I generated a new pair on my laptop, and uploaded the new public key to Ubuntu One, and I am still being asked for a password. I have tried the password for my Ubuntu account and any other password it could have been.

        I then got the monitor and keyboard out to see if I could reset the keys directly on the pi. It boots to a screen where there are some sha256 hashes related to the ssh key and a prompt that all I need to do to ssh into the box is type "ssh [EMAIL="UbuntuSSO@192.168.X.XXX"]UbuntuSSO@192.168.X.XXX[/EMAIL]". Not helpful. I cannot figure out how to reach a command line from this screen.

        I am familiar with proper Linux distros and Ubuntu systems, but I am having a very hard time finding resources about Ubuntu Core, because of the lack of market share and the HORRIBLE naming decision. At least you used to be able to put "Snappy Core" in quotes and have a chance of finding something related. The results are so polluted with normal Ubuntu issues.

        Any help would be appreciated. All I want to do is to reset the ssh keys.. Bonus if you can tell me how to just replace the whole ssh key system with a password like a normal person. At a minimum, I think I can figure it out if I can just get to a command line on the pi.

---

### Post by TheFu on 2017-10-07
Take the microSDHC out of the pi.  Put it into a real computer. Mount the storage.  Remove the ~/.ssh/ directory or just mv that directory so you can put it back if things don't work better.

Put it back into the Pi and reboot.

I'm not sure I'd want a device inside my LAN to get authentication from an external SSO provider.  Just sayin'.

---

### Post by BL86vYR on 2017-10-24
> **TheFu said:**
> Take the microSDHC out of the pi. Put it into a real computer. Mount the storage. Remove the ~/.ssh/ directory or just mv that directory so you can put it back if things don't work better.

        Put it back into the Pi and reboot.

        I'm not sure I'd want a device inside my LAN to get authentication from an external SSO provider. Just sayin'.

        Can you elaborate on that last bit? It seems like Ubuntu Core is based on the idea of authenticating via external SSO by default.
        Are you saying that Canonical has done a stupid thing (because where will these Ubuntu Core devices be that is not inside of a LAN?), and you muddying the waters with some opinion that you hold?
        Or are you giving me actionable advice?

        I would love to replace the paired ssh key system with a password, but I have no clue how to do that.

---

### Post by TheFu on 2017-10-24
I'm saying that I wouldn't want core authentication to anything on my corporate LAN coming from outside the LAN, from systems I don't control.  Whether you consider that "actionable" or not is something you need to decide.  Just providing an opinion.

What happens when your WAN connection is down? Can you still get into all the systems?  For how long?  I don't know the answers to these questions.

If I was providing services to external people, who aren't on the corporate network already, then wouldn't be nearly as concerned.  If the networking is down, then the authentication can be down too. Nothing is lost to them.

I'm a huge fan of using keys over passwords.  IMHO, using passwords generally means we've already lost the security wars.

Did you get the ~/.ssh/ removed?

---

### Post by BL86vYR on 2017-10-24
Ubuntu Core 16, as a product developed by Canonical, has this external authentication infrastructure on by default, so... Canonical put out a stupid product I guess?

        I'm just running a dinky Nextcloud server for syncing contacts and calendar with my devices. It sits under my couch. I don't have and will never have port 22 open to the outside and any ssh password I would have would be very long, so I'm not sure what value I am getting out of the keys, other than having to maintain them. If the Canonical servers ever go down, I would just have to follow your advice from earlier. If the networking is down, then the Nextcloud server has no point anyways.

        I didn't get your advice in time, so I just pulled all the data off of it and nuked/paved. BUT I just checked and now I'm being asked for an ssh password that doesn't exist, so I will now need to utilize your advice. Thank you for answering my question!

---

### Post by TheFu on 2017-10-24
[https://docs.ubuntu.com/core/en/guides/manage-devices/index](https://docs.ubuntu.com/core/en/guides/manage-devices/index) - explains how to create a system user that can login with a userid and password on Ubuntu Core.

---

### Post by BL86vYR on 2017-10-25
PERFECT. Thank you so much!

---

