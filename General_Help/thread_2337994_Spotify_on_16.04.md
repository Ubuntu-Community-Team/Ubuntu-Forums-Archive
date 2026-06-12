---
title: "Spotify on 16.04"
date: 2016-09-23
forum: General Help
---

### Post by Billingd on 2016-09-23
Hi

I am struggling to get spotify working reliably in 16.04. I have downloaded the libraries libgcrypt11 and used the packages for linux directly from spotify, having followed the advice about using the encryption key. Spotify looks like it has installed ok, but wont always start. Sometimes it does but mostly it doesnt. It just sits there with a blank window. Anyone got any advice please how to debug or re-install for a more reliable experience ?

Many thanks


David

---

### Post by Billingd on 2016-09-26
Hi

I have undeleted spotify - wiping out all config files and dependencies; then re-installed from the bash script provided by spotify.com. I got no errors during installation. Unfortunately still suffering this problem. Sometimes Spotify starts, but about 50% of the time it doesn't and I just get a blank window. A reboot sometimes works though in this case.
Dont know if it makes a difference but its lubuntu 16.04 I'm using. Worth saying though that spotify was rock solid on lubuntu 15.04 that I've just upgraded from. 
Any ideas ?

David

---

### Post by howefield on 2016-09-27
Installed it on stock Ubuntu 16.04 and can't replicate an issue, rock solid every time even if only for the last day or so.

Try starting Spotify from the terminal and log the output to a text file with something like..

```
spotify &> ~/Documents/spotify.txt
```

That will create a text file in your Documents folder that might contain some clues after a failed start.

---

### Post by Billingd on 2016-09-27
Hi

Thanks for your suggestion. I have created a couple of text files - one from a failed Spotify start and, following a reboot, one from a successful Spotify start. Both outputs contain errors. I can't see anything obvious myself to explain the difference in functionality though. I thought I might be able to attach them in this forum but the upload manager is complaining they're too big. Surprising as they're only 21kb each. 
I'm thinking of dropping down to an earlier Spotify version and trying that. I noticed earlier that the version that I had in 15.04 wasn't the current latest version


David

---

### Post by howefield on 2016-09-27
> **Billingd said:**
> ...- one from a failed Spotify start and, following a reboot, one from a successful Spotify start. Both outputs contain errors.
 
```
grep -i "ERROR" "/home/$USER/Documents/spotify"
```

amend the path accordingly and that might narrow the output down, check for sensitive info (there shouldn't be - but you might get username or artists/titles ect in the original output).

---

### Post by Billingd on 2016-09-27
Hi

With a bit of luck, these will now attach. They look identical, but I assure you they have come from separate files .....
No. Despite being the same size, the fail output still wont attach. You'll have to take my word for it that it looks the same, and has the same errors within it

Regards


David[ATTACH]271375[/ATTACH]

---

### Post by Billingd on 2016-09-27
Let me try in a seperate post[ATTACH]271376[/ATTACH]

---

### Post by howefield on 2016-09-28
Sorry, nothing discernible as fatal. Always hard to pin point an intermittent fault.

Hopefully you'll get something from your thread on the spotify forum, but in the meantime I'd suggest the webplayer, not sure how complete and featured it is but it works.

[https://play.spotify.com](https://play.spotify.com)

---

### Post by Billingd on 2016-09-28
Hey

Thanks. I didn't even know there was a spotify web player. That's great

Many thanks


David

---

### Post by howefield on 2016-09-28
> **Billingd said:**
> Thanks. I didn't even know there was a spotify web player. That's great

Cool, you're welcome.

There is an annoying "I am not a Robot" feature to navigate on sign in, but easy enough to get past. Other than that triviality, it serves me well enough.

---

