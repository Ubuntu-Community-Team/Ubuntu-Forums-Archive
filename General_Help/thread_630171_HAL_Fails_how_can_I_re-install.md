---
title: "HAL Fails how can I re-install?"
date: 2007-12-03
forum: General Help
---

### Post by thenetduck on 2007-12-03
HI HAL fails for some odd reason (not sure how this happend) how can I fix it or reinstall hal to work or at least reconfigure it. 

thanks 

the net duck

I solved my problem. Here is how I did it.

If your HAL fails, you can do two things. 

1: restart it
2: re-install it

Now HAL works with dbus to control your mounted whatevers. To restart it, just do this....

```

sudo /etc/init.d/dbus restart

```

to re-install hal (don't recommend doing this because it will un-install other programs sometimes..

got to synaptics and just uninstall it. then install it again or check the reinstall. 

Hope this helps someone.

The Net Duck

---

