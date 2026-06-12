---
title: "&quot;Create Launcher&quot; question...."
date: 2007-08-10
forum: General Help
---

### Post by Glake on 2007-08-10
I know the title is vague. Sorry about that.

This is what I am trying to do. I created a launcher to run rkhunter and chkrootkit in the terminal. 

this is the command I am using " sudo rkhunter -c " and " sudo chkrootkit "

It works fine, the terminal opens and rkhunter runs, but closes as soon as it is done.

I know this is going to be simple. But what can I add to the command to keep the terminal open after rkhunter or chkrootkit is done scanning? (or any other launcher I create,) That way I can easily just scroll up the terminal and see if all is OK. 

I am also asking this because I recently installed Ubuntu on someones computer and they are new to Linux and Ubuntu. I am trying to set a few things up so he doesn't have to type in commands in the terminal.

Thanks

---

### Post by olejorgen on 2007-08-10
Ok, probably not optimal, but works:
```

bash -c "<your command> ; read"

```

---

### Post by Glake on 2007-08-10
> **olejorgen said:**
> Ok, probably not optimal, but works:
```

bash -c "<your command> ; read"

```


Thanks I will try this shortly.

---

