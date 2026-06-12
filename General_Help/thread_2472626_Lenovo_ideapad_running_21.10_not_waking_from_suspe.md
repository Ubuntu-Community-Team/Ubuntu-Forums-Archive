---
title: "Lenovo ideapad running 21.10 not waking from suspend"
date: 2022-03-06
forum: General Help
---

### Post by katrinayellow on 2022-03-06
Hi everyone

First time posting, I'm returning to Ubuntu after a Mac "holiday". Hopefully I describe this problem properly - please let me know if I must provide more info. 

I have a new Lenovo Ideapad 5. My issue is that the computer does not wake up from suspend - I have to hard power it down, and then start it again (the power light blinks but does nothing no matter what is pressed or clicked). It does this either after being told to suspend, or after the lid closes, or if I leave it inactive for long enough (even though I have automatic suspend off, and display blank screen set to never). It does it when I have the NVidea drivers set to 510 or to 470, and whether I'm using the Nvidea drivers or Nouveau. It did it when on 20.04,  and is now doing it on 21.10. It did it when I edited some configuration file to change the option for close lid (sorry I'm so vague, I've tried so many things, half of them I don't understand).

I've seen from a ton of reading that not waking from suspend seems to be an issue with Lenovo and Ubuntu, so clearly a bad combination. The computer is not a dual boot - so there is no switching to linux from windows in the bios needed (or possible), and other options suggested to make changes in the bios aren't there. Given I know so little (I ran Ubuntu for years but a long time ago, and I wasn't an expert) I'm starting to try solutions which I don't even know what they do - I just try them and hope. 

Does anyone have any advice? There are a ton of similar questions but none of the solutions I have tried have worked. 

Hopefully thanks in advance!

---

### Post by katrinayellow on 2022-03-06
Replying to this myself for anyone else needing to see it - a fix which finally worked was updating my kernel from 5.13 to 5.16.12, and then also further changes had to be made - see the answer to the question in this thread: [https://askubuntu.com/questions/1389585/how-do-i-install-kernel-5-15-7-on-ubuntu-21-10-impish-indri](https://askubuntu.com/questions/1389585/how-do-i-install-kernel-5-15-7-on-ubuntu-21-10-impish-indri)
Finally!

---

### Post by JAlexoid on 2022-06-09
Try resetting BIOS, works much more often that I'd like to.

---

