---
title: "How to change display settings from the command line?"
date: 2021-05-06
forum: General Help
---

### Post by sixblue on 2021-05-06
I have an old Dell Inspiron 6400 that I've hooked up to run some instruments. I use it both locally and via ssh. Lubuntu, lsb-release -a shows Ubuntu 18.04.5 LTS. After an ssh session where I was running some python code remotely (with a tk GUI if that's relevant), the laptop screen seems to have switched to an incompatible setting (see image below). The boot screen is normal (also below), and the blue Lubuntu splash screen with the little dots that fill themselves in also shows up normally (on boot and on shutdown), so I'm pretty confident there's nothing wrong with the hardware. After editing the grub file over ssh I can boot to command line and log in that way, so I have access both from the machine itself and remotely. startx brings me to the same messed up screen as before. You can't tell from the image, but it's trying to display a window, it's just badly smeared to the right as you go down (and I can actually see the pointer arrow which is not distorted at all). I can't seem to forward the display any more over ssh (e.g. can't get xeyes etc to work, errors out after a while with Can't open display, whether I use 0.0 or IP:0.0) although it's been a while since I've had time to work on this and I may be forgetting something (tried on two different machines, using xming and cygwin-X).

TL/DR: I have local and remote command line access and I want to reset the laptop's display settings so I can use the desktop again

thanks!

[IMG]https://attachments.office.net/owa/mdungrin%40ucalgary.ca/service.svc/s/GetAttachmentThumbnail?id=AAMkAGEzNjNiNGUyLTg0NTgtNDU5Ny04NGQ2LTkxODY1NGQ3ZGUwMQBGAAAAAACIxuPVqpILS5O4%2BrSk1lSDBwBybG7xbRCcRICFUqhr54CMAACYq8hYAABx%2Fs8gti50QIjUgXoPRiKdAASY%2BmsoAAABEgAQAIw48UuY8QNFnzIgKuax58s%3D&thumbnailType=2&token=eyJhbGciOiJSUzI1NiIsImtpZCI6IjMwODE3OUNFNUY0QjUyRTc4QjJEQjg5NjZCQUY0RUNDMzcyN0FFRUUiLCJ0eXAiOiJKV1QiLCJ4NXQiOiJNSUY1emw5TFV1ZUxMYmlXYTY5T3pEY25ydTQifQ.eyJvcmlnaW4iOiJodHRwczovL291dGxvb2sub2ZmaWNlLmNvbSIsInVjIjoiNTUyMzEwNmI3Mzk2NDg5NDk4ZTRlMTgzNTE1MmIwZTYiLCJzaWduaW5fc3RhdGUiOiJbXCJrbXNpXCJdIiwidmVyIjoiRXhjaGFuZ2UuQ2FsbGJhY2suVjEiLCJhcHBjdHhzZW5kZXIiOiJPd2FEb3dubG9hZEBjNjA5YTBlYy1hNWUzLTQ2MzEtOTY4Ni0xOTIyODBiZDkxNTEiLCJpc3NyaW5nIjoiV1ciLCJhcHBjdHgiOiJ7XCJtc2V4Y2hwcm90XCI6XCJvd2FcIixcInB1aWRcIjpcIjExNTM4MzYyOTYzNDUyODUxOTZcIixcInNjb3BlXCI6XCJPd2FEb3dubG9hZFwiLFwib2lkXCI6XCJlMzliOGYwZS03YzMzLTRiYTgtYTFjOC1kM2Y0YjhmMzY5OThcIixcInByaW1hcnlzaWRcIjpcIlMtMS01LTIxLTM5NzE5NTY3OC0xOTY5Njg2MjMxLTIyMjY0NjU5MC03NzU1OTEwXCJ9IiwibmJmIjoxNjIwMzM3NDUxLCJleHAiOjE2MjAzMzgwNTEsImlzcyI6IjAwMDAwMDAyLTAwMDAtMGZmMS1jZTAwLTAwMDAwMDAwMDAwMEBjNjA5YTBlYy1hNWUzLTQ2MzEtOTY4Ni0xOTIyODBiZDkxNTEiLCJhdWQiOiIwMDAwMDAwMi0wMDAwLTBmZjEtY2UwMC0wMDAwMDAwMDAwMDAvYXR0YWNobWVudHMub2ZmaWNlLm5ldEBjNjA5YTBlYy1hNWUzLTQ2MzEtOTY4Ni0xOTIyODBiZDkxNTEiLCJoYXBwIjoib3dhIn0.axVmzZNimERBPjVWpaQDF9ah7t7EQpFAJDx4ONfVFxaYeecSk9DR-6JlJ9ixKWQRqeyXJApDGCysjHPoNTpk1gG6HvpnWTyach_Gn0R_TlLVUkoqufsDKVU-4b3rk_2NaTuhZSb7FtIDzqLyHZVRgoh-2KOByUNkH3YxtjXK8jVR9tryyCWWt4CMql5tDMbj93ovdAcGOPlbuS0-QMtfVn2VLeYOTtimCAX3snCvojMJ_oPaubB9aNZ6qB97gVhF8T-5G4GFmDCW6IwyVn35ogwNJYSAilRu24btsPSpJRF2ovK-1TOnsYdwCOlXNe0ZcW4YCKk3CGow7iU0FocqPw&X-OWA-CANARY=2UrA4TLU-0ChNSuvpFA2fyDT4XTYENkYmM7paPdQAaelJ41YfH0SJ2WapTiXJee9_o_iQfgQTmw.&owa=outlook.office.com&scriptVer=20210419002.04&animation=true[/IMG][IMG]https://attachments.office.net/owa/mdungrin%40ucalgary.ca/service.svc/s/GetAttachmentThumbnail?id=AAMkAGEzNjNiNGUyLTg0NTgtNDU5Ny04NGQ2LTkxODY1NGQ3ZGUwMQBGAAAAAACIxuPVqpILS5O4%2BrSk1lSDBwBybG7xbRCcRICFUqhr54CMAACYq8hYAABx%2Fs8gti50QIjUgXoPRiKdAASY%2BmsoAAABEgAQAD2W4gjNVi1BjVLHBus9s0c%3D&thumbnailType=2&token=eyJhbGciOiJSUzI1NiIsImtpZCI6IjMwODE3OUNFNUY0QjUyRTc4QjJEQjg5NjZCQUY0RUNDMzcyN0FFRUUiLCJ0eXAiOiJKV1QiLCJ4NXQiOiJNSUY1emw5TFV1ZUxMYmlXYTY5T3pEY25ydTQifQ.eyJvcmlnaW4iOiJodHRwczovL291dGxvb2sub2ZmaWNlLmNvbSIsInVjIjoiNTUyMzEwNmI3Mzk2NDg5NDk4ZTRlMTgzNTE1MmIwZTYiLCJzaWduaW5fc3RhdGUiOiJbXCJrbXNpXCJdIiwidmVyIjoiRXhjaGFuZ2UuQ2FsbGJhY2suVjEiLCJhcHBjdHhzZW5kZXIiOiJPd2FEb3dubG9hZEBjNjA5YTBlYy1hNWUzLTQ2MzEtOTY4Ni0xOTIyODBiZDkxNTEiLCJpc3NyaW5nIjoiV1ciLCJhcHBjdHgiOiJ7XCJtc2V4Y2hwcm90XCI6XCJvd2FcIixcInB1aWRcIjpcIjExNTM4MzYyOTYzNDUyODUxOTZcIixcInNjb3BlXCI6XCJPd2FEb3dubG9hZFwiLFwib2lkXCI6XCJlMzliOGYwZS03YzMzLTRiYTgtYTFjOC1kM2Y0YjhmMzY5OThcIixcInByaW1hcnlzaWRcIjpcIlMtMS01LTIxLTM5NzE5NTY3OC0xOTY5Njg2MjMxLTIyMjY0NjU5MC03NzU1OTEwXCJ9IiwibmJmIjoxNjIwMzM3NDUxLCJleHAiOjE2MjAzMzgwNTEsImlzcyI6IjAwMDAwMDAyLTAwMDAtMGZmMS1jZTAwLTAwMDAwMDAwMDAwMEBjNjA5YTBlYy1hNWUzLTQ2MzEtOTY4Ni0xOTIyODBiZDkxNTEiLCJhdWQiOiIwMDAwMDAwMi0wMDAwLTBmZjEtY2UwMC0wMDAwMDAwMDAwMDAvYXR0YWNobWVudHMub2ZmaWNlLm5ldEBjNjA5YTBlYy1hNWUzLTQ2MzEtOTY4Ni0xOTIyODBiZDkxNTEiLCJoYXBwIjoib3dhIn0.axVmzZNimERBPjVWpaQDF9ah7t7EQpFAJDx4ONfVFxaYeecSk9DR-6JlJ9ixKWQRqeyXJApDGCysjHPoNTpk1gG6HvpnWTyach_Gn0R_TlLVUkoqufsDKVU-4b3rk_2NaTuhZSb7FtIDzqLyHZVRgoh-2KOByUNkH3YxtjXK8jVR9tryyCWWt4CMql5tDMbj93ovdAcGOPlbuS0-QMtfVn2VLeYOTtimCAX3snCvojMJ_oPaubB9aNZ6qB97gVhF8T-5G4GFmDCW6IwyVn35ogwNJYSAilRu24btsPSpJRF2ovK-1TOnsYdwCOlXNe0ZcW4YCKk3CGow7iU0FocqPw&X-OWA-CANARY=qUzqLlzaT0GrcpZobr0cadBZsLPYENkYjcQoFiz-ovwE_Ob21YEJOyQAOg9gcAGuuStbVi02mTw.&owa=outlook.office.com&scriptVer=20210419002.04&animation=true[/IMG]

---

### Post by guiverc on 2021-05-06
Are you aware that flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors), so you're asking about a release that only days ago reached it's EOL.

- [https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/](https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/)
- [https://lubuntu.me/bionic-5-released/](https://lubuntu.me/bionic-5-released/)

which mentioned the 3 years and support ending April-2021.

The latest Ubuntu Weekly Newsletter highlights the EOL of *flavors*
- [https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue681#Lubuntu_18.04_LTS_End_of_Life_and_Current_Support_Statuses](https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue681#Lubuntu_18.04_LTS_End_of_Life_and_Current_Support_Statuses)
(or on this forum see [https://ubuntuforums.org/showthread.php?t=2461582](https://ubuntuforums.org/showthread.php?t=2461582))

Not all flavors gave EOL notices, but if you look they had dates provided already. eg. Xubuntu mentioned on [https://xubuntu.org/release/18-04/](https://xubuntu.org/release/18-04/) that EOL was 29-April-2021 (more accurately than Lubuntu's April-2021).

FYI: As warned on the Lubuntu forum/discourse, I've been moving wiki pages so they aren't reporting as Lubuntu any longer (search engine searches however using historical pages names may result in errors) however searches performed on wiki.ubuntu.com or help.ubuntu.com will find them. Lubuntu only uses and supports the LXQt desktop now.


FYI:  *I used a `dell inspiron 6400 (cduo-t2450, 2gb, intel 945gm)` in QA-testing releases up to 19.04 (i386) and later 18.04.5 (August 2020), but that box has since been recycled as it was x86/i386 only  (I still use i386 boxes; whilst slower & pentium M, I much preferred them)*

---

