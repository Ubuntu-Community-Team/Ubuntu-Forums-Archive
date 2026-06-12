---
title: "Make uppercase accent (french) with keyboard"
date: 2023-12-15
forum: General Help
---

### Post by paulouxps3 on 2023-12-15
Hello, 
I searched a solution to my problem and I could not find anything.
I  was using ubuntu 23.04 (lunar lobster) and everything was working fine  with my keyboard. However, I updated ubuntu to 23.10 (mantic minautor)  and my keyboard has now changed. The problem is with the "é" and letters  like that in capital. Before, I needed to press Cap.lock and then press  the "é" key and it would do the capital letter (É, made by copy-paste).  Now it is just doing the lowercase "é". I also tried different keyboard  configurations available in the parameters but none are working. Some  are doing the lowercase "é" and some the number 2. Some keyboard  configuration allow to do the uppercase "é" but with AltGr or things  like that which are not practical. 

How to get this  functionnality back please ? As a french who need the write a lot of  text it is very important for me to have it.

Again, pardon me if  the question has already been asked but I could not find it. My english  is also not perfect and I hope you will understand my problem.

Paul.

---

### Post by arphnut on 2023-12-16
---- French version below ---

Hello,

A bug was reported to ask ubuntu ([https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/2035076](https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/2035076)).
Apparently it was solved and updating mutter should do the work (with "apt install mutter").

--- version française ---
Bonjour,

Un bug a été signalé sur AskUbuntu, et le problème a été réparé sur la dernière version de mutter.
Il te suffit de mettre à jour mutter (avec "apt install mutter" puis de redémarrer ton PC) pour régler le problème.

---

### Post by vanadium on 2023-12-16
@arphnut You will not update mutter with the command you provided. Please remove that advice from your answer, and others, please do not follow that advice. "mutter" will only be updated if it is being updated in the software repository of your distribution. It that is the case, the update will automatically be pushed to your computer upon the next update.

As I see the bug report, there is no indication that the bug correction may be backported to 11.10. However, the correction will certainly come with the next Ubuntu version in April, which will be a Long Term Release.

---

