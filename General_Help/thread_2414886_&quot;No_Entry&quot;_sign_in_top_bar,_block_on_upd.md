---
title: "&quot;No Entry&quot; sign in top bar, block on update manager"
date: 2019-03-16
forum: General Help
---

### Post by Richard_York on 2019-03-16
I'm running Ubuntu 14.04 LTS on an Acer Aspire 32 bit laptop with Intel® Core™2 Duo CPU T5550 @ 1.83GHz × 2. Probably at least 12 years old.

Currently there's a "no entry" red circle with white bar road sign in the top bar; when  clicked, it displays an error message and tells me to run the package manager. 
When I open this, a box comes up with the same error message as that in the top bar:

> E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

When I close this, the Package Manager closes itself.

Somewhere along the way, a box opens telling me this is a serious error and needs reporting. Meanwhile we can't run updates, of course.

So I don't know what to do next. I could open the terminal, but have no idea what to ask of it, nor what to do about any advice it may return.
Thanks for any help.

---

### Post by oldos2er on 2019-03-16
Please run ```
sudo apt update
``` and post the complete output here.

---

### Post by Impavidus on 2019-03-17
The full output of```
sudo apt update
```would be nice.

Furthermore, Ubuntu 14.04 will reach end of life next month. Instead of upgrading, it may be a better idea to skip version 16.04 and try a clean install of 18.04. I also suggest to check the health of your hard drive: [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools). It may be best to do so using a live disk. It wouldn't be surprising if the hard drive of your laptop was failing after 12 years.

---

### Post by Richard_York on 2019-03-18
Thanks, I'll do this.
I'll try the health check too.

I realise the machine's probably near the end of its useful life, and am fairly sure it'll throw up its hands in horror if I try 18.04 on it - still worth a try! 
 Maybe Lubuntu or Xubuntu might keep it happy?

Meanwhile I'll try the code in the terminal.
Thanks again,

---

