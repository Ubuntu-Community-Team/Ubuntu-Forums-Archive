---
title: "Can't update, GPG error"
date: 2013-04-13
forum: General Help
---

### Post by prc292 on 2013-04-13
HI,

i just installed 12.10 on a compaq 6510b laptop. im getting these gpg errors

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/Release](http://security.ubuntu.com/ubuntu/dists/quantal-security/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.

i have tried dozens of solutions from the net and nothing will work. im starting to think that this may be related to the public wifi here at school. it does require a web-logon for access. anyone know if this is a possibility. and if so is there anyway to get around this problem.

thanks for any ideas on this.

---

### Post by kurt18947 on 2013-04-13
I'm not sure if this would help but it's easy to try and no harm that I'm aware of.  Try a different software source.  I'm using gnome-shell and can switch repositories via Synaptic or the software and updates app.  I'm cautious about software sources but as long as the mirrors are not cracked I don't believe there is a significant risk.  Several universities host mirrors as well as some U.S. Gov't facilities (Argonne Nat'l Labs is one).  Plus it lessens the bandwidth load for Canonical.

---

### Post by prc292 on 2013-04-13
Tried 2 different servers but still no luck just cant seem to get a key for this one server. cant install some software or updates. gotta get this figured out. ive tried both ubuntu and mint on this laptop. both are giving me the same errors for gpg keys.of course im pretty sure it's the same server on both distros but, thats what made me think that this was related to my network connection. i havent had the chance to try a different wifi connection yet but will be doing that today. ill post the results back.

---

### Post by prc292 on 2013-04-13
Alright im on a different wifi network and the problem is still there.

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/Release](http://security.ubuntu.com/ubuntu/dists/quantal-security/Release)  

so both Ubuntu 12.10 and Mint 14 get the same errors while updating. i Realize that these distros are very similar and i believe the problem is occuring on the same server for both, But 2 different installs having the same problem leads me to believe that this is a problem on the server. Could be wrong but....Not sure what else it could be. i have tried swithching the server for software soureces to every available option for the U.S...so Im lost on this. Please any ideas/help/info would be greatly appreciated. I've done 3 clean installs on this laptop in the past 24 hours. im sick of windows. Really dont want to be stuck with it anymore.

---

### Post by wildmanne39 on 2013-04-13
*Thread moved to **General Help**.* This is not an wifi issue, you are missing the security key for some package you are trying to install.
Thankshttp://ubuntuforums.org/editpost.php?p=12601727&do=editpost

---

### Post by wildmanne39 on 2013-04-13
Changed title to be descriptive of the issue you are having so you will be more likely to get the help you need.

---

### Post by prc292 on 2013-04-13
Thanks for moving this. i realized that this turned out to be a different issue than i first suspected with the wifi i was on but didnt know how to move this or even if i could. Well the good news is the issue seems to be gone with the help of these commands.


 sudo -i
 apt-get clean
 cd /var/lib/apt
 mv lists lists.old
 mkdir -p lists/partial
 apt-get clean
 apt-get update

This was one of the first solutions i found on the net while searching for a solution and i tried it multiple times, but for some reason it just worked this time. Not sure but the problem seems to be solved. Thank you for suggestions.

---

### Post by wildmanne39 on 2013-04-13
Your welcome! No you can not move a thread or change the title that has to be done by a moderator.

---

