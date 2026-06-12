---
title: "Ubuntu security server either extremely slow or inaccessable!"
date: 2014-07-02
forum: General Help
---

### Post by roachk71 on 2014-07-02
Hello, everybody,

Over the past month or so I have noticed that the **security.ubuntu.com** server has been either timing out, slowing to a dialup-esque speed (or halt), or is simply inaccessable. There's a kernel update I've been trying repeatedly to install, and I can't even attempt downloading it without the server connection timing out. :evil:

My questions:
[LIST]
[*]Is this server experiencing internal problems, or is it possibly under a DDoS attack? 
[*]Is anybody else experiencing this issue, and, if so, which ISP or cable/DSL provider is being used? 
[/LIST]

Any assistance with this issue would be greatly appreciated, since it could possibly compromise security on our Boxen.
Oh, the provider part of the second question is important, by the way: this information could help determine whether said provider is, for whatever reason, throttling or blocking access. I'm on Time-Warner Cable.

Many Thanks :KS

---

### Post by uRock on 2014-07-02
Have you tried selecting a different server via Software Sources? If not, then open Ubuntu Software Center, then click **Edit**, then click **Software Sources**, then in the **Download from** dropdown select **Other**, then in the new window click the **Select Best Server** button.

---

### Post by roachk71 on 2014-07-02
Sorry, but I use Mint 17, which doesn't give me the best server selection option.

---

### Post by ian-weisser on 2014-07-02
Then try another mirror at random.
My security updates remain blindingly fast.

---

### Post by roachk71 on 2014-07-02
Is there a mirror for the _security.ubuntu.com_ server? This is the one I'm having difficulty with. The remaining servers are working fine.

---

### Post by slickymaster on 2014-07-02
Try these ones:
[http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/)
[http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/)

---

### Post by roachk71 on 2014-07-02
Thank you, slickymaster. The British archive server seems to have fixed that issue. :D

---

### Post by slickymaster on 2014-07-02
Glad you got it fixed.

---

