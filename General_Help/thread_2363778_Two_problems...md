---
title: "Two problems.."
date: 2017-06-14
forum: General Help
---

### Post by aartjansen on 2017-06-14
Hi, struggling with an issue with remmina. I am 90% sure its to do with a certificate in the known_hosts file, and I want to delete the file to find out. However everywhere points to ~/.freerdp as the folder. And the problem is I don't have that folder. I also tried using find . -iname 'known_hosts' with no result. and locate -i known_hosts with no result.

I did find a file in /root/.ssh/known_hosts but I don't know how to open the location to see if its the right file.

Second issue is this forum doesn't accept my usual email address. I've seen this before as its a newer domain, but the email address is perfectly valid. its 
[email]me@mydomain.computer[/email]
Thanks for any advice, in advance.

Ok I found a /.config/freerdp/known_hosts2 deleting it didn't fix my problem.

---

### Post by steeldriver on 2017-06-14
Hello and welcome to the forums

For your second issue, you should start a new thread in the [Resolution Center sub-forum]("https://ubuntuforums.org/forumdisplay.php?f=123")

For the first question, please be more specific about what issue you are having exactly and how you came to the conclusion that it relates to a known_hosts file

---

### Post by aartjansen on 2017-06-14
Well basically I installed the newest version of remmina I could. Added entries for remote systems I monitor (Windows SBS) which use RD gateway, got prompted to ok a certificate on one where I forgot to tick use TLS & ignore certificates. Since then it simply fails to connect, (unable to connect to RDP server) even though the settings are correct, other similar systems work ok, and the windows PC next to this one connects fine to that same remote server.

---

