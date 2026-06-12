---
title: "Can cPanel be installed on Ubuntu 20.04 ?"
date: 2022-04-09
forum: General Help
---

### Post by satimis on 2022-04-09
Can cPanel be installed on Ubuntu 20.04 ?

On Internet search I found following links;

1)
How to install cPanel on Ubuntu 20.04 LTS
[https://support.cpanel.net/hc/en-us/articles/4404304825623-How-to-install-cPanel-on-Ubuntu-20-04-LTS](https://support.cpanel.net/hc/en-us/articles/4404304825623-How-to-install-cPanel-on-Ubuntu-20-04-LTS)

2)
How to Install cPanel on Ubuntu 20.04
[https://linux-id.net/install-cpanel-on-ubuntu-20-04/](https://linux-id.net/install-cpanel-on-ubuntu-20-04/)

However also I found information, saying cPanel doesn't work on Ubuntu.

Please advise.  Thanks

Regards

---

### Post by CharlesA on 2022-04-09
According to the official instructions, it works but it's still in testing, so not ready for production.

It looks like they download a shell script and execute it to get cPanel installed.

If you have the resources, why not spin up a virtual machine (using VirtualBox, KVM, whatever) and test it out?

---

### Post by satimis on 2022-04-09
> **CharlesA said:**
>  - snip -
If you have the resources, why not spin up a virtual machine (using VirtualBox, KVM, whatever) and test it out?

It is a good idea.  I'll test it on Ubuntu 20.04 VM later.

I'm planning installing cPanel on my new AMD Ryzen 9 5900X PC running Ubuntu 22.04 as host and guest.  I'm waiting for the release of Ubuntu 22.04 and then I'll build the new PC.

I'm also aware that the release of AMD 7000X is just around the corner.

Regards

---

### Post by mIk3_08 on 2022-04-09
> **satimis said:**
> Can cPanel be installed on Ubuntu 20.04 ?
On Internet search I found following links;
1)How to install cPanel on Ubuntu 20.04 LTS
[https://support.cpanel.net/hc/en-us/articles/4404304825623-How-to-install-cPanel-on-Ubuntu-20-04-LTS](https://support.cpanel.net/hc/en-us/articles/4404304825623-How-to-install-cPanel-on-Ubuntu-20-04-LTS)
2)How to Install cPanel on Ubuntu 20.04
[https://linux-id.net/install-cpanel-on-ubuntu-20-04/](https://linux-id.net/install-cpanel-on-ubuntu-20-04/)
However also I found information, saying cPanel doesn't work on Ubuntu.
Please advise.  Thanks
Regards
Yes. Definitely it will work. Just make sure that you are using the server released one. Just install it via command line. ssh with your static ip. Good luck and regards.

---

### Post by satimis on 2022-04-09
> **mIk3_08 said:**
> Yes. Definitely it will work. Just make sure that you are using the server released one. Just install it via command line. ssh with your static ip. Good luck and regards.
Thanks for your advice.

I'll install the server release.

I'll test installing cPanel on a Ubuntu 20.04 deskop VM, running command lines on Terminal.

On my new PC, also I'll install cPanel on Ubuntu 22.04 desktop VM.  If it works I'll install it on a bare-metal Ubuntu 22.04 desktop SSD.  Then I'll clone/install my live sites on the SSD.  There are 36 websites running on HostGator server.

Regards

---

### Post by mIk3_08 on 2022-04-10
> **satimis said:**
> Thanks for your advice.
I'll install the server release.
I'll test installing cPanel on a Ubuntu 20.04 deskop VM, running command lines on Terminal.
On my new PC, also I'll install cPanel on Ubuntu 22.04 desktop VM.  If it works I'll install it on a bare-metal Ubuntu 22.04 desktop SSD.  Then I'll clone/install my live sites on the SSD.  There are 36 websites running on HostGator server.
Regards
You're always welcome. Good Luck and Cheers. Happy Linux Computing.

---

### Post by satimis on 2022-04-12
> **mIk3_08 said:**
> You're always welcome. Good Luck and Cheers. Happy Linux Computing.
Hi,

I haven't tested it yet.  I'm now fully engaged on other Linux computing.

I'm planning testing it on Ubuntu 22.04 on a new AMD Ryzen 9 PC which will be built after Ubuntu 22.04 released.

I'll come back posting the test result here.

Regards

---

