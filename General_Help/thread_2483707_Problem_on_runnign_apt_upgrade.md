---
title: "Problem on runnign apt upgrade"
date: 2023-02-07
forum: General Help
---

### Post by satimis on 2023-02-07
Hi all,

Ubuntu 22.04

On running;
$ sudo apt upgrade ```

....
The following security updates require Ubuntu Pro with 'esm-apps' enabled:
  imagemagick libopenexr25 libmagickcore-6.q16-6-extra libmagickwand-6.q16-6
  imagemagick-6.q16 libmagickcore-6.q16-6 imagemagick-6-common
...

```

Pls advise how to fix the problem?  Thanks

Regards

---

### Post by monkeybrain20122 on 2023-02-07
Here is the answer, you need a subscription for that feature.

[https://askubuntu.com/questions/1452299/im-getting-the-message-the-following-security-updates-require-ubuntu-pro-with](https://askubuntu.com/questions/1452299/im-getting-the-message-the-following-security-updates-require-ubuntu-pro-with)

---

### Post by varunendra on 2023-02-07
It's normal. No need to fix unless you need 10 years professional support, something like Red Hat Enterprise.

---

### Post by satimis on 2023-02-07
> **monkeybrain20122 said:**
> Here is the answer, you need a subscription for that feature.

[https://askubuntu.com/questions/1452299/im-getting-the-message-the-following-security-updates-require-ubuntu-pro-with](https://askubuntu.com/questions/1452299/im-getting-the-message-the-following-security-updates-require-ubuntu-pro-with)
Hi,

Thanks for your advice.

Is it FREE to subscribe ?

Regards

---

### Post by satimis on 2023-02-07
> **varunendra said:**
> It's normal. No need to fix unless you need 10 years professional support, something like Red Hat Enterprise.
Thanks for your advice.

Whether leaving following packages```

imagemagick libopenexr25 libmagickcore-6.q16-6-extra libmagickwand-6.q16-6
  imagemagick-6.q16 libmagickcore-6.q16-6 imagemagick-6-common

```
not updated?

Regards

---

### Post by ActionParsnip on 2023-02-07
[https://www.omgubuntu.co.uk/2023/01/ubuntu-pro-general-availability](https://www.omgubuntu.co.uk/2023/01/ubuntu-pro-general-availability)

---

### Post by varunendra on 2023-02-07
> **satimis said:**
> Thanks for your advice.

Whether leaving following packages```

imagemagick libopenexr25 libmagickcore-6.q16-6-extra libmagickwand-6.q16-6
  imagemagick-6.q16 libmagickcore-6.q16-6 imagemagick-6-common

```
not updated?

Regards

I think the replies given in the link posted by monkeybrain20122 in post#2 above give all the answers you want.

DISCLAIMER: Below is my personal understanding, which may be wrong.

This is something new from Ubuntu, and somewhat confusing for most users. My personal understanding from what I've read in a quick search -
[LIST=1] It is an "Additional Support Stream", optional, not mandatory. It just offers something extra that was earlier not offered to normal users.
[*] Everything that was supported previously is still supported like before.
[*] In your case, the suggested packages are security patches to packages that come from 'Universe' repository. Earlier, security packages were not offered for these. Now they are, if you really need or 'want' them.
[*] If you use your computer for personal use, or any kind of use that does not need very serious security, there is nothing you need to do or worry about. This is just for extra security that was offered only to "Ubuntu Advantage" users earlier. Now, if really needed (for example on those machines that can be a hot target for cyber-attacks), a normal user can get those security patches too, for free, for upto 5 machines, following the method given in the link posted by monkeybrain20122's post above.
[/LIST]

Hope it clears at least some of the doubts many users may have.

---

### Post by satimis on 2023-02-07
> **varunendra said:**
> I think the replies given in the link posted by monkeybrain20122 in post#2 above give all the answers you want.

DISCLAIMER: Below is my personal understanding, which may be wrong.

This is something new from Ubuntu, and somewhat confusing for most users. My personal understanding from what I've read in a quick search -
[LIST=1] It is an "Additional Support Stream", optional, not mandatory. It just offers something extra that was earlier not offered to normal users.
[*] Everything that was supported previously is still supported like before.
[*] In your case, the suggested packages are security patches to packages that come from 'Universe' repository. Earlier, security packages were not offered for these. Now they are, if you really need or 'want' them.
[*] If you use your computer for personal use, or any kind of use that does not need very serious security, there is nothing you need to do or worry about. This is just for extra security that was offered only to "Ubuntu Advantage" users earlier. Now, if really needed (for example on those machines that can be a hot target for cyber-attacks), a normal user can get those security patches too, for free, for upto 5 machines, following the method given in the link posted by monkeybrain20122's post above.
[/LIST]

Hope it clears at least some of the doubts many users may have.
Hi Varun,

Lot of thanks for your detail advice.

I have 3 drives in this PC running Ubuntu 22.04

1) This drive - 2 TB NVMe Pcie 3.0 SSD running VirtualBox
2) 1 TB NVMe Pcie 3.0 SSD  running VirtualBox
3) 500G SSD running KVM

Only this drive popup that warning on running Update and Upgrade.  The other 2 drives don't have this problem on running Update and Upgrade.  I wonder whether it is caused by the previous problem encountered by me in setting Static IP on this drive.  Please refer to following posting;

**[COLOR="#FF0000"][SOLVED] About set up Static IP on LAMP server[/COLOR]**
[https://ubuntuforums.org/showthread.php?t=2483189&highlight=satimis](https://ubuntuforums.org/showthread.php?t=2483189&highlight=satimis)

Other 2 drives are also running Static IP

Regards

---

### Post by varunendra on 2023-02-08
> **satimis said:**
> ....Only this drive popup that warning on running Update and Upgrade.  The other 2 drives don't have this problem on running Update and Upgrade.  I wonder whether it is caused by the previous problem encountered by me in setting Static IP on this drive...

Didn't read the thread linked by you, but this is not related to IP addressing or any "problem". Most likely, the other two setups may not have imagemagick package installed, hence no update/patching required. You can check by -
```
dpkg -l | grep imagemagick
```
..on all 3 setups. You should get something like -
```
ii  imagemagick....
```
..on the machine in question. If my guess is correct, the other two won't have it installed (no output from dpkg command above). If you do get same or similar outputs though, I'd like to see that, plus the outputs of -
```
cat /etc/os-release
uname -mr
```
..from all 3 machines to see if there is any difference.

In any case, be assured that it is nothing to worry about unless your VM in question is in some serious attack vector (that is, something that the entire world is desperate to hack! :) ).

---

