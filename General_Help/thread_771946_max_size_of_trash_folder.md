---
title: "max size of trash folder"
date: 2008-04-28
forum: General Help
---

### Post by nricci on 2008-04-28
Hello all,

Coming from windows, I'm used to let the trash folder manage itself. I setup its max size and forget.

Is this something we can do in Ubuntu? How? Where?

Thanks for any help!

---

### Post by justleen on 2008-04-28
your trash is just a folder, with no specific limit.

---

### Post by Oldsoldier2003 on 2008-04-28
of course you could always set a script to empty the trash folder and cronjob it to run every day or every x hours... or whatever interval you want

---

### Post by nricci on 2008-04-28
Thanks Justleen.

Well, at least in this particular regard, Windows has an advantage.

With Ubuntu I can see the trash folder size increasing to a point where it starts to damage disk performance. It's just one more thing for you to pay attention and manage.

In Windows, that is not necessary.

But I'll keep trying.

Thank you for taking the time to answer.

---

### Post by nricci on 2008-04-28
Thank you Oldsoldier2003.

That's not what I want to do. 

I want to setup a max size for trash (50 MB, for example) and forget about it. The folder would manage itself in a fifo fashion.

Windows does just that. When you delete something, Windows permanently deletes the oldest stuff in trash to release some space for what's coming.

All you have to do is define how much space you want for trash (10% of partition size? 5%?) 

Thank you for the cron idea.

---

### Post by Mr Frosti on 2008-04-28
I have written a quick Ruby script that will look in your trash folder and delete files inside until a certain threshold. Download and unzip the attachment, and give the file execute permissions. This script can be called like this:

```
ruby /path/to/script -s <size>
```

Where <size> is the size (in MB) that you would like to keep the Trash folder at.

Using this script, create a crontab entry (run crontab -e) like follows to run the script every 5 minutes:

```
5 * * * * /path/to/script -s <size>
```

The power of Linux is its flexibility. The recycle option in Windows  only allows you to delete a recycling bin based on size, but with Linux, we can setup any condition that we want via a little scripting. For example, where is the Recycling Bin even at on Windows? Its not even a real folder...

---

