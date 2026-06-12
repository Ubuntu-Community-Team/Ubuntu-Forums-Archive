---
title: "startup programs don't start?"
date: 2006-12-23
forum: General Help
---

### Post by khughitt on 2006-12-23
Hello!

I am new to the forum, and there is a bug I've been trying to figure out for a while now, but have not had any luck on google, or the other forums i use. I was wondering if anyone here might be able to help out :)

For some reason, if i add commands to "sessions --> startup programs", they don't always start up when i load ubuntu. At first i noticed it because the beryl window manager wouldn't load by itself, so i had to manually run "beryl-xgl" every time i logged in. I originally thought it was a problem with xgl, but then i realized that it wasn't just beryl, but other commands that wouldn't execute on start up. i tried writing a script to wait 15 seconds and then run the command, and adding the script to startup programs, but the script doesn't get run either (doh!)

anyways.. anyone else have similar problem? any ideas on why this is happening?

any help is appreciated,
Thanks !

---

### Post by hanzomon4 on 2006-12-23
I've had this happen with kiba-dock, don't know why... As for beryl add beryl-manager not beryl-xgl

---

### Post by khughitt on 2006-12-23
i have beryl-maanger as well. its not just a certain few programs, it happen to just about anything i try to load up.

---

### Post by khughitt on 2007-01-01
/bump.. still no luck. anyone?

---

### Post by Disastorm on 2007-01-03
YO type in:
sudo chown -R <your username> ~/

in the console! It worked for me and I had the exact same problem!

---

### Post by khughitt on 2007-01-04
bummer- still no luck. thanks for the suggestion though. that's strange that changing the ownership of all the files in your home directory would have an effect on which programs start-up. It wouldn't be the first time however that the solution to a problem has been something seemingly unrelated :P

---

### Post by quartzy on 2007-01-04
> **pwnedd said:**
> bummer- still no luck. thanks for the suggestion though. that's strange that changing the ownership of all the files in your home directory would have an effect on which programs start-up. It wouldn't be the first time however that the solution to a problem has been something seemingly unrelated :P

That isn't as unrelated as you implied.  If at startup time your user tried to run a script owned by root it would probably get a permission denied error :p

---

### Post by randomnumber on 2007-01-05
Dumb question, but are you certain that the startup programs are enabled. There is an enable/disabled button.

---

### Post by khughitt on 2007-01-05
> **randomnumber said:**
> are you certain that the startup programs are enabled. There is an enable/disabled button.

thanks for the suggestion. i checked though and they are all enabled.

---

