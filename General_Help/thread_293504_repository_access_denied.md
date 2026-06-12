---
title: "repository access denied"
date: 2006-11-05
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2006-11-05
Ok, I am gonna ask for help one more time before I completly wipe out hard drive and start over(lose all the work I've put into this) Here is the problem:: When I go to System>Administration>Synaptic Package Manager STAY WITH ME- Ok, now I click Settings>Repositoies. Here's the problem: Repository window flashes quickly and then gone.An error message pops up saying::repositories list has changed. Please click reload. So I reload and when I go to Settings>Repositories I get a repeat of:: Repository window flashes quickly and message telling me to reload again and it reloads the same 47 packages each time. Please help me as I really do not want to start from scratch. I am using the dapper live ship it cd at this moment

---

### Post by d3v1ant_0n3 on 2006-11-05
What are you trying to do with your repos? If you're wanting to add a new one or remove one, you can input this command into the terminal:

sudo gedit /etc/apt/sources.list

Then put in your password, and gedit will load up the text file that contains all your sources.

---

### Post by IusedTObeSOMEONEelse on 2006-11-05
Thank you for responding I understand that and I have no problem using terminal. I can not recieve updates through update manager and its rather annoying that I can not access repo through synaptic and the reload of the **same 47 packages** I just like to know whats going on in my machine. Is there not a way to fix this from live cd?. Should I just act like there is no problem and igmnore and never be able to access repo through synaptic?

---

### Post by taurus on 2006-11-05
> **MustangSallydd said:**
> Thank you for responding I understand that and I have no problem using terminal. I can not recieve updates through update manager and its rather annoying that I can not access repo through synaptic and the reload of the **same 47 packages** I just like to know whats going on in my machine. Is there not a way to fix this from live cd?. Should I just act like there is no problem and igmnore and never be able to access repo through synaptic?
Here we go again, eh!!!

```

sudo aptitude update
sudo aptitude upgrade

```

---

### Post by IusedTObeSOMEONEelse on 2006-11-05
And Good Morning To You taurus, don't you ever sleep down there in  Sunny Land? It is still troubling to me this whole repo's drama.

---

### Post by taurus on 2006-11-05
Got about 5 hours of shut eyes and it's not so sunny outside right now, windy and heavy overcast.  We need some rain (a lot of rain) since we are way behind in the total amount of rainfall for the year...

It doesn't happen to my Edgy at all about the repos in synaptic so not sure exactly why on your machine.  Again, you can either not worry about it and use aptitude from a terminal or you can drive yourself insane trying to figure out what's the problem with it!

---

### Post by IusedTObeSOMEONEelse on 2006-11-05
Some thing I did try was: I put in a dapper sources list and did the upgrade yada yada and when i went to Synaptic>Settings>Repositories, the same thing with the quick flash of repo's window and same message about repo's list change and that I should reload.

---

### Post by taurus on 2006-11-05
You are running Edgy right!  Try not to mix between Dapper and Edgy in /etc/apt/sources.list because it's not a real good thing to do.  Things will break left and right and before you know it, you would have a one real sick machine...  ;)

---

### Post by IusedTObeSOMEONEelse on 2006-11-05
Here's what I'm gonna do, this my main machine so I am gonna put my sources list back together with edgy(yikes) and hope nothing broke. I have set up an older machine to play with Feisty and no matter what I do it has not broken! Go figure that one. So off I go to play. By the way taurus, I spent 22 years in Orlando and I miss it!!8)

---

### Post by taurus on 2006-11-05
If you need a copy of /etc/apt/sources.list that I use, just let me know and I will include it here...

Mickey Mouse town!!!  :rolleyes:

---

### Post by IusedTObeSOMEONEelse on 2006-11-05
Thaqnks so much taurus> Great moral support :-D  I gave up on that machine for now and I' gonna work on this machine today. They don't seem to be doing much on the Feisty front. But I can still tweak on it. I love that saying 'If it's not broke, fix it till it is' cause I'll keep fixen'. Have a good one!

---

### Post by taurus on 2006-11-05
If you don't have any important files on your Edgy, try reinstall it from fresh to see if you still have problems with adding repo to synaptic!  

Good luck.

p.s.  Has the race started yet?

---

### Post by IusedTObeSOMEONEelse on 2006-11-05
you mean those crazy fools that wanna run in the cold? I haven't checked yet. ok, I am on both machines I only have a dapper disc and I have it in and its at the partition part. now I can give the whole hard drive to ubuntu (40) GBif I want as I do not know what is best. So it is asking me now: Resize IDE 1 master, partition #1(hda1) and use freed space or Erase disk: IDE 1 master (hda) -41.1 GB Maxtor 2F040J0 or  Manually edit partition table.  what would be the recomended way to go.

---

### Post by taurus on 2006-11-05
If you want an easy way out, let the install handle the whole partition thing.  I believe it will create two partitions for you: /dev/hda1 for / and /dev/hda5 for swap.

Yes, I mean those crazy fools running in the cold in shorts.  I was one of those crazy fools a few years back, 1998, when I ran in it.  :twisted:

---

### Post by IusedTObeSOMEONEelse on 2006-11-05
ok so it says new partion size 57% (20.2GB) does that mean that the old down load is still there as well

---

### Post by taurus on 2006-11-05
Did you tell it to use the whole entire disk?

---

### Post by IusedTObeSOMEONEelse on 2006-11-05
I haven't did anything yet. that is what it is recomending

---

### Post by taurus on 2006-11-05
Yip since you don't have anything else on your harddrive.  Let it use up the whole harddrive and just sit back and watch the Live NYC Marathon on tv...  :twisted:

---

### Post by IusedTObeSOMEONEelse on 2006-11-05
will do. thanks taurus. i'm through monopolizing your time.I am just gonna let it do it's thing Thanks, by ;)

---

### Post by taurus on 2006-11-05
That's alright.  Other questions are kind of way over my head anyway!

---

### Post by TheRingmaster on 2006-11-05
you shouldn't double post [http://www.ubuntuforums.org/showthread.php?t=292505](http://www.ubuntuforums.org/showthread.php?t=292505)

---

### Post by IusedTObeSOMEONEelse on 2006-11-05
Youn are correct, some times I get so impatiant. taurus has really tried to help me. But I find it hard to believe that there wasn't an easier solution to the problem other than a total system reload and I gave plenty of time before I gave in.

---

