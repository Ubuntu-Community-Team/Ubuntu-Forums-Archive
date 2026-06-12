---
title: "Update and internet issues"
date: 2016-11-14
forum: General Help
---

### Post by brupsilva on 2016-11-14
I just installed Ubuntu on my Desktop for the first time. After I finished, I did the update by the Updater and in some moments it says that there is no connection to the internet. But the browsers work just fine. Through the terminal it does not access. It tries to access an IP and it stays forever in the 0% until giving error in some addresses. "0% [Connecting to br.archive.ubuntu.com (200.236.31.4)"
I do not understand what happens. I installed the same in my notebook and everything rolls fine.

[ATTACH=CONFIG]272128[/ATTACH]

---

### Post by ian-weisser on 2016-11-14
What kind of connection to the internet are you using?
The symptoms you describe often occur when connecting through a proxy. Like a school or corporate network proxy.

---

### Post by Impavidus on 2016-11-15
Completely unrelated, but note that when you use **sudo su** to become root, there is no longer need for sudo in front of apt-get, as you are already root. Or if you use **sudo apt-get** there is no need to become root first. So you can skip the sudo su command.

---

