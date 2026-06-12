---
title: "possible fiell system error"
date: 2008-03-03
forum: General Help
---

### Post by onesojourner on 2008-03-03
I have an ext3 filesystem that I need to check for errors. How should I go about doing that. During boot up it would try to mount and detect an error and then it would fail to mount it. I have since reinstalled and it is mounting again but I would like to make sure everything is ok with it.

---

### Post by ruy_lopez on 2008-03-03
If it's mounting fine, leave it alone. But if it ever fails to mount again, run fsck on the device associated with it. Just make sure it isn't mounted when you run 'fsck'.

---

