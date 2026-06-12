---
title: "Problems with monodevelop"
date: 2014-11-06
forum: General Help
---

### Post by Martin_Schmid on 2014-11-06
Hello,


since yesterday I'm having a problem with monodevelop. During an update of my packages my laptop lost power. After running 

```

sudo apt-get update
sudo apt-get upgrade

```

Monodevelop stopped working. When I try to reinstall it, I get the following error:

```

sudo apt-get install monodevelop

```

The following packets have unmet dependencies:

monodevelop: Depends on libmetacity-private0a (>= 1:2.34.0), but should not be installed.
Problems can't be solved, you have defect packages.

^ translated freely from german.

If I try

```

sudo apt-get install libmetacity-private0a

```

I get the following:
libmetacity-private0a : Depends on metacity-common (= 1:3.12.0-0~eugenesan~trusty5) but 1:3.12.0-1ubuntu3.01~eugenesan~trusty1 should be installed.
 

To me it seems like the repository is faulty, but I'm not sure.

Any input will be greatly appreciated.

---

### Post by ringstaart on 2014-11-06
Try running another sudo apt-get update. If that doesn't solve it, simply waiting until all the packages in the repositories are properly up-to-date probably works. It's annoying, but at least it's not permanent.

That doesn't mean that there are no immediate solutions.

---

### Post by Martin_Schmid on 2014-11-06
Okay, but waiting till the problem fixes itself is not the ideal solution for me. Anything else?

Thanks for your comment.

---

### Post by kurt18947 on 2014-11-06
I am not an expert at all but here might be something to try if you haven't.  I've run into interrupted updates/upgrades causing problems. That sounds like what happened to you.  If you have synaptic installed, you could try Edit -> fix broken packages and see if there are any problems found.  I've also had apt-get  -f  sometimes help.  I expected either solution would fix a problem.  Not always though, sometimes one works, sometimes the other.

---

### Post by ringstaart on 2014-11-06
> **kurt18947 said:**
> I am not an expert at all but here might be something to try if you haven't.  I've run into interrupted updates/upgrades causing problems. That sounds like what happened to you.  If you have synaptic installed, you could try Edit -> fix broken packages and see if there are any problems found.  I've also had apt-get  -f  sometimes help.  I expected either solution would fix a problem.  Not always though, sometimes one works, sometimes the other.

Oh right, I forgot about that.

Try "sudo apt-get -f install monodevelop". If that doesn't work, you could try "sudo apt-get --fix-missing install monodevelop".

---

### Post by Martin_Schmid on 2014-11-07
Thanks a lot guys. Sadly, nothing worked. Looks like I'm in for a reinstall, because I really need mono asap.

---

