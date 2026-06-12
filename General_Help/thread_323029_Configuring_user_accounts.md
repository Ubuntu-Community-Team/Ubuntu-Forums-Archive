---
title: "Configuring user accounts"
date: 2006-12-21
forum: General Help
---

### Post by lolwhites on 2006-12-21
Is there a way of configuring the accounts on my computer so that when someone else logs in, they see the same things I do (I'm the administrator). For example, when my partner logs in she gets the basic Firefox, not my version, which has add ons I downloaded. Do I have to manually download the same add ons for her  version of Firefox so she can use them too?

---

### Post by kidders on 2006-12-21
Hi there,

You probably installed the add-ons on a per-user basis, in which case the most straightforward thing to do might be to copy your ~/.mozilla into your wife's home directory. She'd wind up with a duplicate of your own Firefox profile, internet cache & bookmarks, etc. included ... which you could then remove, if you wanted to.

See if this works for you:
```
sudo cp -dpR /home/user1/.mozilla /home/user2
sudo chown -R user2:user2 /home/user2/.mozilla
```

Your wife's Firefox should, of course, not be running at the time.

**Edit:** Afaik you can install Firefox extensions system-wide ... in future, you could try doing that, although I've never needed to, so I could only guess about how to do it. I'm sure it's straightforward enough though.

---

