---
title: "Update manager crash, apport crash"
date: 2014-04-01
forum: General Help
---

### Post by Futant on 2014-04-01
Hello there! Hoping for some help with a rather irritating problem which started last night. I am running Ubuntu 12.04 on a Dell XPS l502x, things generally go pretty smoothly but last night when I used the GUI update button, the update manager crashed, then when I went to look at the crash details apport crashed too. Tried again a few times with the same result. Then I used 
```
sudo apt-get update
```
and
```
sudo apt-get upgrade
```
the fist command worked fine, no errors. The second also had no errors, but as far as I can tell also did not upgrade anything. 'Reading package lists' got to 100% and then the process ended (with no error messages).

I then left it for the night in the hope that everything would have fixed itself in the morning, but alas no. Same problem today. Opening the update manager (and the software centre, and synaptic) leads to it crashing, which in turn leads to apport crashing. If I open them using the terminal I get a lot of parsing errors and then a final segmentation error, which is where the process ends.

I would be happy using the CLI to update and install but to me it looks like that isn't working either, despite the lack of error messages.

I looked through some log files, but am a bit lost when it comes to finding the one relating to the update manager. [Here ]("http://pastebin.com/3XrpQmLD")is apport.log, which log files would be helpful in working out what's wrong with updating? Let me know what info you need.

Thanks!

EDIT: Definitely something wrong somewhere, just tried to install [SWI Prolog]("http://www.swi-prolog.org/") for a course that I am doing. Added the PPA fine, but installation exits (with no error message) after 'reading package lists' reaches 100% (or very close, hard to tell). Only got a few days for this part of the course so if anyone can help, please do!

---

### Post by ibjsb4 on 2014-04-01
try

```
sudo apt-get -f install
```

---

### Post by Futant on 2014-04-02
Hey thanks for the reply, the command executes fine but hasn't had any effect. Have had missing dependencies/broken packages etc before but this issue doesn't seem like that. One thing I left out of my first post is that when I choose 'check for updates' from the top bar, it will get a few % through then give me this:
```

Task cannot be monitored or controlled

The connection to the daemon was lost. Most likely the background daemon crashed.

Details:
It seems that the daemon died.

```

Don't know if that's any use. [Here]("http://pastebin.com/fUxmQXhE") is a syslog as well, Any other log files which might be helpful?

---

### Post by ibjsb4 on 2014-04-02
I'm not good at reading logs :( try reinstalling your update manager.

```
sudo apt-get install --reinstall update-manager-core update-manager
```

---

### Post by Futant on 2014-04-03
Cheers, no luck there though either. It seems that every operation I try gets as far as finishing reading the package lists then just quits, with no error messages. I have been searching for any help on this but don't seem to be getting anywhere!

---

### Post by Futant on 2014-04-03
Well, the problem has been resolved, possibly though disabling apport (though it's probably a coincidence). Tried apt-get update for the umpteenth time and this time, it worked! As did upgrade. Update manager, synaptic and the software centre are all working. Hooray! Thanks for helping :)

---

