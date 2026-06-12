---
title: "rsync backup script is not executed by cron"
date: 2015-01-16
forum: General Help
---

### Post by mc-rpg on 2015-01-16
Good afternoon people, I KNOW rsync & cron issues are regularly posted on these forums and I have spent the last three days going through a lot of the answers (that are tweaks of the same thing more than radically different) and nothing has worked, the issue is I have is with the following script FS.sh:
```
#!/bin/sh
#PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
#ENV=/root/.bashrc
#SHELL=/bin/sh
#PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
#rsync -avh --delete -e ssh /media/Files/Documents/ root@192.168.1.11:/volume1/Disk1/Documents/
/usr/bin/rsync -avh --delete -e ssh /media/Files/Documents/ root@192.168.1.11:/volume1/Disk1/Documents/
#/usr/bin/rsync -av --delete -e "/usr/bin/ssh -i /home/MyUser/.ssh/id_rsa" /media/Files/Documents/ root@192.168.1.11:/volume1/Disk1/Documents/
#rsync -av --delete -e "ssh -i /home/MyUser/.ssh/id_rsa" /media/Files/Documents/ root@192.168.1.11:/volume1/Disk1/Documents/
date > ~/time_tmp
```

I left commented several of the tweaks I have made to the same command just so you're aware of them (there have been a lot more than the ones there though), none of those worked. At first cron seemed to not be running at all, because my only command was the rsync command. Later I added the *date > ~/time_tmp* and indeed, cron was running the script after all! The time_tmp file was created everytime but the rsync command got completely ignored for reasons that have eluded me completely. All the commands have worked when I execute the script manually. Right now, this is the cron job, generated using gnome-schedule:
```
*/2 * * * * /home/MyUser/FS.sh # JOB_ID_5
```

I'm on ubuntu 14.04. Any help would be appreciated.

---

### Post by nerdtron on 2015-01-16
So you run the script manually and it runs successfully?

1. If you just run it in the bash terminal, use /bin/bash and not /bin/sh. In Ubuntu, the two are different. So try running the script manually as "bash /home/myuser/script.sh"
2. If it is a bash script, replace the first line of the script as "#!/bin/bash"
3. In cron, the first line of the script is crucial since you did not specify the shell it would run. Now I think it run on /bin/sh, so to for the script to run on the bash shell, update the cron to "*/2 * * * * /bin/bash /home/myuser/script.sh"
4. Create a log for your rsync command or log for the script itself so that you can see what cron outputs when it runs the script. Something like: "*/2 * * * * /bin/bash /home/myuser/script.sh 2>&1 /tmp/log_file.txt"

Everything I presented here is just like being explicit on what you want to do. Sometimes the defaults on your current terminal/shell is different from cron enviroment.

---

### Post by mc-rpg on 2015-01-21
> **nerdtron said:**
> Everything I presented here is just like being explicit on what you want to do. Sometimes the defaults on your current terminal/shell is different from cron enviroment.

It turned out I didn't need to be that explicit. Is just that the cron environment won't be able to provide the passphrase for the RSA key. It seems that that fact alone was causing me a lot of pain :mad:. Long story short, I went the keychain route but it still needed you to provide the passphrase every time you restarted your machine so I thought about it and decided to sacrifice the extra security of the passphrase in exchange of convenience. Besides this there were configuration issues on the NAS side but that's irrelevant to the ubuntu side.

This is how my command ended up looking in the end and it works:
```
rsync -avh --delete -e ssh /path/to/Music/ myusername@mynassaddress:/path/to/Music/
```

---

