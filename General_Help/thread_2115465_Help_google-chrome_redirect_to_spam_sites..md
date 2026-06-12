---
title: "Help google-chrome redirect to spam sites."
date: 2013-02-13
forum: General Help
---

### Post by odror on 2013-02-13
I thought that linux was safe.  Once every few clicks I am redirected from google chrome browser to a spam site. I have reinstalled chrome with no change. On windows there are tools to deal with that. Any ideas how to fix that on Ubuntu. Thanks

---

### Post by carl4926 on 2013-02-13
Are you using Chrome signed in to your Google account?

---

### Post by odror on 2013-02-13
> **carl4926 said:**
> Are you using Chrome signed in to your Google account?
yes

---

### Post by carl4926 on 2013-02-13
Then I suggest you do a house clean...

For example. If you create a New User and login
Try Chrome as it is, not logged in to your account. Is it OK?

With Chrome closed: In your normal login, if you put this folder
.config/google-chrome/
In the trash and start chrome, it should be clean, not logged in. And should work fine.

Can you confirm the above?

---

### Post by odror on 2013-02-13
> **carl4926 said:**
> Then I suggest you do a house clean...

For example. If you create a New User and login
Try Chrome as it is, not logged in to your account. Is it OK?

With Chrome closed: In your normal login, if you put this folder
.config/google-chrome/
In the trash and start chrome, it should be clean, not logged in. And should work fine.

Can you confirm the above?
I have installed 3 spam blocker. It took care of the problem. I have also taken your suggestion removing the .config/google-chrome/ directory and starting fresh. I'll keep you posted if the problem returns.

Do you think that this represent a more serious security breach? or it is just spam ads.

Thanks

---

### Post by carl4926 on 2013-02-13
It sounds like your google account, that stores all your browsing history/cookies etc.. has become tainted.

If you use your browser to visit certain sites we'll not mention here, you might want to consider using a different browser that isn't logged in and that you can clean all history without concern

---

### Post by odror on 2013-02-13
> **carl4926 said:**
> It sounds like your google account, that stores all your browsing history/cookies etc.. has become tainted.

If you use your browser to visit certain sites we'll not mention here, you might want to consider using a different browser that isn't logged in and that you can clean all history without concern

So far so good. It was probably something in the .config/google-chrome. Possibly an extension or add-on that was installed without my permission.

The strange thing about the problem was that it started while visiting "safe" sites like google, major news sites and my local machine web pages. It was like a "time bomb" that issues spam on regular intervals regardless of the visited site. It started today.

---

### Post by carl4926 on 2013-02-13
Not had any trouble myself
But hope it remains good for you

---

