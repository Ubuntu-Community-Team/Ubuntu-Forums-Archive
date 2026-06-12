---
title: "Cannot run gksu nautilus"
date: 2014-07-21
forum: General Help
---

### Post by humanracer on 2014-07-21
Hi I used foremost to try and recover some deleted files but I cannot seem to access or delete the recovered folder as it is locked. The path is home/recovered. Someone suggest that I try gksu nautilus but I get the error 

ERROR:nautilus-window.c:2116:nautilus_window_get_slots: assertion failed: (NAUTILUS_IS_WINDOW (window))



Any ideas? Thank you.

---

### Post by jjclonker on 2014-07-21
You could use "sudo nautilus" (no quotes).

Disclaimer: I am not responsible for any damages or any problems that this may cause.

Accessing your root system can be dangerous if you accidentally change or delete something that you shouldn't have.

---

### Post by mooreted on 2014-07-21
Open a command prompt and either change the permissions of the folder and the files in it or move it to a folder you control.

To change the folder to be accessible by anyone:

sudo chmod -r ugo+rwx /home/recovered

Then you can access the files with a normal Nautilus session.

You can also move the folder to your home folder.

sudo mv /home/recovered /home/<username>

So that, if I were to use my username it would be:

sudo mv /home/recovered /home/mooreted

If you just want to delete the folder you can:

sudo rm -rf /home/recovered

WARNING: rm -rf will delete anything and everything you tell it to. If you aren't careful you could delete everything on your hard drive!

---

### Post by wildmanne39 on 2014-07-22
It is a really bad idea to run an GUI app with sudo it can become owned by root and then it will not be accessible.

Also rm -rf is very dangerous and should be avoided in its current form if possible like already said one typo and you could delete your whole hard drive. 

Please be careful when about telling people to do these two things.

I received that same error message but it still worked.

---

### Post by mooreted on 2014-07-22
I use dangerous commands every day, you just have to realize they are dangerous and check it before you hit Enter. The command line is amazingly powerful and as they say, "with great power comes great responsibility". But I don't think people should be afraid to use that power sensibly.

---

### Post by wildmanne39 on 2014-07-22
Please read the rules about these kind of commands before posting them.
[http://ubuntuforums.org/announcement.php?f=326](http://ubuntuforums.org/announcement.php?f=326)
You did a good job of including a warning but remember there will be new people that will totally mess up their system because they will only read the part about the command and not about the warning, I am saying is we need to be careful when posting such commands.

---

### Post by humanracer on 2014-07-22
Thanks it worked. I will be careful in regards to what files I delete.

---

### Post by jjclonker on 2014-07-22
Thank you for pointing that out Wild Man. I had no idea that their were regulations set on that sort of thing, but it makes sense, and thank you very much for your concern.
I will read that link you posted Wild Man.
I was by no means trying to cause any problems. I am here to help not hurt.

NOTE: I have used these commands many times with no issues, but yes, if not handled with extreme caution they can be very destructive.

---

### Post by QIII on 2014-07-22
When giving instructions on the forum, I prefer to use mv rather than rm.  That way the files can be recovered if need be and removed after it is clear the poster's issue is resolved.

---

### Post by jjclonker on 2014-07-22
Very good point there QIII.
Thank you.

---

### Post by deadflowr on 2014-07-22
> **QIII said:**
> When giving instructions on the forum, I prefer to use mv rather than rm.  That way the files can be recovered if need be and removed after it is clear the poster's issue is resolved.

I tend to cp the file to my documents folder as a simple backup, then proceed to mv or rm.
That way I at least still have an uncorrupted file, if needed later.

For whatever it's worth, though, I believe "sudo -H <command>" is a suitable way to run as an alternative to gksu.

---

### Post by Frogs Hair on 2014-07-22
You can use the following to get gksu working and those using Ubuntu Tweak will already have the package installed as a dependency.  

```
sudo apt-get install gksu
```

---

