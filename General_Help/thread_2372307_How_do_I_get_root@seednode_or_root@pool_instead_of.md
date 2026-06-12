---
title: "How do I get root@seednode or root@pool instead of what normally comes up in terminal"
date: 2017-09-23
forum: General Help
---

### Post by ninjagod on 2017-09-23
[IMG]https://scontent-lhr3-1.xx.fbcdn.net/v/t31.0-8/21950812_134131300659180_8273633596814062013_o.jpg?oh=290bddb29a508ba20f7347d0a98adb6c&oe=5A517A10[/IMG]

I need to get the two terminals on the left. How can i do this?

Thanks

---

### Post by mörgæs on 2017-09-23
The root account is disabled by default and with good reasons. Please read [here]("https://help.ubuntu.com/community/RootSudo") before you consider going that route.

---

### Post by uRock on 2017-09-23
This should be helpful, [http://ubuntuhandbook.org/index.php/2016/06/change-hostname-ubuntu-16-04-without-restart/](http://ubuntuhandbook.org/index.php/2016/06/change-hostname-ubuntu-16-04-without-restart/) 

That will help you change the hostname. As pointed out, root is disabled by default.

---

### Post by ninjagod on 2017-09-23
Thanks but this doesnt really help. I am trying to follow this tutorial [https://www.youtube.com/watch?v=kVPcmirqyOY](https://www.youtube.com/watch?v=kVPcmirqyOY) but he doesnt explain how he has managed to get those terminals. Could you please break it down for me into steps? 

Thanks again!

---

### Post by efflandt on 2017-09-23
That guy is so quiet I can't hardly hear him. And it is part 6 of a series, so I don't know what he did leading up to that.

But I think those other terminals are connected to some other computer(s) or cryptocurrency server and logged into that or those (possibly using ssh?). That is why they show different hostnames in the prompts.

---

### Post by ninjagod on 2017-09-23
I connected the DNS seed node to my external IP. Would I still be able to connect and open up a shell using SHH for my external IP? or does it have to be some kind of specialised server. Thanks

---

### Post by oldos2er on 2017-09-23
> **ninjagod said:**
> I need to get the two terminals on the left. 

Can you explain why?

```
sudo -i
``` will give you a root shell which you can leave open for as long as you need it; use it wisely.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ninjagod on 2017-09-23
Ok but how do i connect via SSH

---

### Post by ian-weisser on 2017-09-23
Have you ever used SSH before?
If not, see [https://ubuntuforums.org/showthread.php?t=1656263](https://ubuntuforums.org/showthread.php?t=1656263) for a Beginner's Guide to SSH

---

### Post by ninjagod on 2017-09-23
Yes, I have now figured out how to use SSH. When i connect, i can connect to three different ip addresses. I was just getting confused because my name in the terminal was staying the same. Does anyone know how he managed to change the names in each terminal for each individual ssh connection? It would be quite confusing if i was trying to work on three different terminals with different SSH connections when they all had the same name :D. Also, do you know how to connect via SSH as a root user??

Thanks

---

### Post by mörgæs on 2017-09-23
> **ninjagod said:**
> Also, do you know how to connect via SSH as a root user?


One can only hope that the server admin did not allow that. 

Please read what has been posted about the root account. I am not convinced that you are fully aware of what root is and does.

---

