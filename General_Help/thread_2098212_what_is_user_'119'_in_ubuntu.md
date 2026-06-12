---
title: "what is user '119' in ubuntu"
date: 2012-12-26
forum: General Help
---

### Post by vksingh on 2012-12-26
Hi All,

I am using Ubuntu 12.10. when i check all my processes using ps -ef command

**119 **      4314     1  0 Dec21 ?        00:00:00 /usr/lib/x86_64-linux-gnu/unity-music-daemon
**119**       4318     1  0 Dec21 ?        00:00:00 /usr/lib/x86_64-linux-gnu/unity-shopping-daemon
**119**       4320     1  0 Dec21 ?        00:00:00 /usr/bin/python3 /usr/lib/unity-lens-photos/unity-lens-photos
**119**       4322     1  0 Dec21 ?        00:00:00 /usr/bin/python /usr/lib/unity-lens-video/unity-lens-video
**119 **      4362     1  0 Dec21 ?        00:00:00 /usr/bin/zeitgeist-daemon
**119**       4369     1  0 Dec21 ?        00:00:00 /usr/lib/zeitgeist/zeitgeist-fts
**119**       4375     1  0 Dec21 ?        00:00:04 zeitgeist-datahub
**119**

can someone please tell me what is user 119 in above.

Thanks,
vivek):P

---

### Post by agillator on 2012-12-26
That depends on your setup. Try checking (BUT NOT CHANGING) the /etc/passwd file. A good way would be less /etc/passwd | grep 119.

---

### Post by Cheesemill on 2012-12-26
> **agillator said:**
> That depends on your setup. Try checking (BUT NOT CHANGING) the /etc/passwd file. A good way would be less /etc/passwd | grep 119.
Or just:
```
grep 119 /etc/passwd
```
:)

---

### Post by rnerwein on 2012-12-26
> **vksingh said:**
> Hi All,

I am using Ubuntu 12.10. when i check all my processes using ps -ef command

**119 **      4314     1  0 Dec21 ?        00:00:00 /usr/lib/x86_64-linux-gnu/unity-music-daemon
**119**       4318     1  0 Dec21 ?        00:00:00 /usr/lib/x86_64-linux-gnu/unity-shopping-daemon
**119**       4320     1  0 Dec21 ?        00:00:00 /usr/bin/python3 /usr/lib/unity-lens-photos/unity-lens-photos
**119**       4322     1  0 Dec21 ?        00:00:00 /usr/bin/python /usr/lib/unity-lens-video/unity-lens-video
**119 **      4362     1  0 Dec21 ?        00:00:00 /usr/bin/zeitgeist-daemon
**119**       4369     1  0 Dec21 ?        00:00:00 /usr/lib/zeitgeist/zeitgeist-fts
**119**       4375     1  0 Dec21 ?        00:00:04 zeitgeist-datahub
**119**

can someone please tell me what is user 119 in above.

Thanks,
vivek):P
hi
if a process is running as root than this process can set a numeric user-id even if that user-id is not present in passwd. but what me confuse is that the init process is the father of all that processes. i can't understand why they all running with user-id 119.
oh sorry there is another way that the father is the init process. if a process was created by fork - fork - exec the father haven't to wait for the child because it will be inherit by the init process as the father. but the matter of fact is ther is something wrong with your passwd.
i guess there is no user with user-id 119 in it and the last user-id in your passwd is 118.
please post back i want to know if i guess wright.
cheers

---

### Post by vksingh on 2012-12-26
I checked the /etc/passwd. Its the guest user which is showing

---

### Post by rnerwein on 2012-12-26
> **vksingh said:**
> I checked the /etc/passwd. Its the guest user which is showing
hi
:confused: where the hell is the guest user coming from. did you made an account for him.
on my boxes - 10.04 and 12.04 there is no guest in the passwd wether in the shadow.
have a look in the shadow if you see something like: 4r18m74QmkB6YNX7bvFh07........
this in the second field of the user guest. 
if there is a password set i would delete the user guest (userdel).
cheers

---

