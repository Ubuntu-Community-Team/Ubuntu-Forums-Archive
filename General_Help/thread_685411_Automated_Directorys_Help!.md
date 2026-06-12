---
title: "Automated Directorys Help!"
date: 2008-02-02
forum: General Help
---

### Post by ectraz on 2008-02-02
Hi, hopeing someone can help im trying to use crontab or something simular to create directorys.
im wanting the names of the directories as the current date d%m%y% for archiving purposes but not getting very far hopeing that someone might have a solution for me.

i think the problem is in that crontab dosent log in as any user therefore dosent have rights to create a directory. can anyone help me with this or point me in the right direction.


Thanks
Clinton Roberts

---

### Post by .nedberg on 2008-02-02
```

mkdir $(date +%Y%m%d)

```

Makes a directory named 20080202 (todays date). You should be able to place that in a script. I would recomend using full path if you want it in your home directory

---

### Post by ectraz on 2008-02-02
I have tryed that directly in crontab and in a script executed from crontab. still no joy :(

---

### Post by .nedberg on 2008-02-02
Are you editing your own crontab via 'crontab -e' or /etc/crontab?

Is the script running at all? You can verify this by adding a line
```

echo something > /home/yourusername/file

```
to your script.

Does the script work? Just run it from shell and see if it works as you want it to.

Is the script executable? 'chmod +x scriptname' will fix that.

I read somewhere that you have to wait two minutes from editing crontab to have it execute any changes. When I test my scripts with crontab I always edit /etc/crontab and schedule them 5 minutes in the future, and I always have one of those 'echo' lines to see if it runs.

---

