---
title: "How to fix &quot;Set the RESUME variable to override this&quot; error/problem?"
date: 2021-09-25
forum: General Help
---

### Post by buiphuc on 2021-09-25
I'm thinking maybe adding the UUID into the "resume" file, or sudo-create it, but the instructions are pretty hard to understand (due to me not being good at English), so maybe anyone could clarify how to so I can understand?

---

### Post by Dennis N on 2021-09-25
Do you mean the file /etc/initramfs-tools/conf.d/resume?
Mine uses a UUID. What does your file look like?
Where are the instructions you refer to?

The UUID in my file is for the swap partition.

---

### Post by buiphuc on 2021-09-25
Yeah, and yep my file also uses a UUID, and the UUID also refers to my swap partition.
The instructions are here: 
                                          [https://www.linuxquestions.org/questions/ubuntu-63/i-set-the-resume-variable-to-override-this-4175656793/](https://www.linuxquestions.org/questions/ubuntu-63/i-set-the-resume-variable-to-override-this-4175656793/)
                                          [https://www.linuxquestions.org/questions/blog/beachboy2-315980/the-initramfs-will-attempt-to-resume-from-dev-sda2-set-the-resume-variable-38193/](https://www.linuxquestions.org/questions/blog/beachboy2-315980/the-initramfs-will-attempt-to-resume-from-dev-sda2-set-the-resume-variable-38193/)
                                          [https://www.f-notes.info/linux:initramfs-tools_resume](https://www.f-notes.info/linux:initramfs-tools_resume)
                                          [https://ubuntuforums.org/showthread.php?t=2401012](https://ubuntuforums.org/showthread.php?t=2401012)
                                          [https://askubuntu.com/questions/1189835/the-initramfs-will-attempt-to-resume-from-dev-dm-1](https://askubuntu.com/questions/1189835/the-initramfs-will-attempt-to-resume-from-dev-dm-1)
Sorry for the late reply, was having school when you replied to my post

---

