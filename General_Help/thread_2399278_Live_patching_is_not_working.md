---
title: "Live patching is not working"
date: 2018-08-23
forum: General Help
---

### Post by defaria on 2018-08-23
I turned on live patching, I know I did, yet I still get "The computer needs to restart to finish installing updates". This has happened a few times. It happened again today so I decided to look into it.

I first thought that perhaps I didn't turn this on so I googled and got to the page that gave me the key. When I went to install that it said it already had a key! See I did set this up before! So I disabled the old key and enabled the new one. Seem to work in that it didn't complain:

```
Earth:sudo snap install canonical-livepatch
snap "canonical-livepatch" is already installed, see 'snap help refresh'
Earth:sudo canonical-livepatch enable 2dfda8886b73445eb2ac40e0ceeb8a51
2018/08/23 09:05:17 error executing enable: Machine-token already exists! Please use 'disable' to delete existing machine-token.
Earth:sudo canonical-livepatch disable
Successfully disabled device. Removed machine-token: bb6c86fae7474985bbfe9979199596fc
Earth:sudo canonical-livepatch enable 2dfda8886b73445eb2ac40e0ceeb8a51
Successfully enabled device. Using machine-token: 06b4fb908268422182c8fd3e98e924da
Earth:canonical-livepatch status --verbose
Command 'canonical-livepatch' is available in '/snap/bin/canonical-livepatch'
The command could not be located because '/snap/bin' is not included in the PATH environment variable.
canonical-livepatch: command not found
Earth:/snap/bin/canonical-livepatch status --verbose
client-version: 8.0.3
machine-id: 3184caadba184b8498e047dc35b202c1
machine-token: 06b4fb908268422182c8fd3e98e924da
architecture: x86_64
cpu-model: AMD Phenom(tm) 9650 Quad-Core Processor
last-check: 2018-08-23T09:06:49.295686432-07:00
boot-time: 2018-08-16T09:11:16-07:00
uptime: 167h59m29s
status:
- kernel: 4.15.0-32.35-generic
  running: true
  livepatch:
    checkState: checked
    patchState: nothing-to-apply
    version: ""
    fixes: ""

Earth:

```

Again, I could have sworn I did this already and yet when I run the update manager sometimes it tells me I need to reboot. What's the deal?

---

### Post by #&amp;thj^% on 2018-08-23
Update manager **_"suggests"_** to restart when kernels are upgraded or some other system packages with services that are marked for reboot when upgraded.

---

### Post by PaulW2U on 2018-08-24
> **defaria said:**
> Again, I could have sworn I did this already and yet when I run the update manager sometimes it tells me I need to reboot. What's the deal?
The following quotes have been taken from: [http://blog.dustinkirkland.com/2016/10/canonical-livepatch.html](http://blog.dustinkirkland.com/2016/10/canonical-livepatch.html)
> The Canonical Livepatch Service is intended to address high and critical severity Linux kernel security vulnerabilities, as identified by Ubuntu Security Notices and the CVE database.
> ...standard (non-security) updates will still require a reboot, as they always have.
My relatively new installation also shows that I've yet to have a livepatch applied but it sounds as if you were expecting more from the service than it actually offers.

---

### Post by defaria on 2018-08-26
That's just skill. Ksplice used to do this. What's the point if you have to reboot?

Not ready for prime time I guess.

---

