---
title: "Failed to get version pid metadata from iplayer site"
date: 2017-04-02
forum: General Help
---

### Post by grey1beard on 2017-04-02
I've installed get-iplayer on a different laptop, 32 bit running 14.04, but when I tried to download a BBC programme using it, and the pid number, as I have done on previuos laptops, I got the error message as per title.
The version that is installed is 2.83, and after googling the problem found various references, but no solution.
Grateful for advice/help.

---

### Post by ajgreeny on 2017-04-02
You really need the updated version of get-iplayer 2.99 from the ppa at [https://launchpad.net/~jon-hedgerows/+archive/ubuntu/get-iplayer](https://launchpad.net/~jon-hedgerows/+archive/ubuntu/get-iplayer)

Follow the instructions on that site to enable the repository, then update and see if that works for you.

Using the pid still works for me on the occasions when a program I want is still available direct on the BBC's own iplayer site but not listed in the get-iplayer cache when I run it, as I did a few days ago with ```
get_iplayer -g --pid=b08j8j2l
```
When using the pid I am not certain you need the -g option but it still works when I added it to the command; try with and without in case changes have been made.

Lots more info at [https://github.com/get-iplayer/get_iplayer/wiki/documentation#recording-with-episode-pid](https://github.com/get-iplayer/get_iplayer/wiki/documentation#recording-with-episode-pid)

---

### Post by grey1beard on 2017-04-02
I  went through the instructions, as per your instructions, but something is missing - possibly past of my brain !
I still have version 2.83 installed, rather than 2.99

The penultimate line in the terminal is always " pid not found in tv cache ".
I tried both of your suggestions, with and without the  -g.

I think I'm just not understanding the method of the final download of 2.99.
I enabled the repository, then ran[I] sudo get-iplayer update
[/I]

 I've looked at the Jon Davies page, then went to the wiki, then the read me file, which sent me back to the Jon Davies page.
So going round in a circle, not spotting some key instruction.

---

### Post by ajgreeny on 2017-04-02
Are you still using Precise, 12.04, as suggested by your info but which I didn't notice before?
The ppa at present will give you version 2.98 for Precise but 2.99 for all the others.
Finally after enabling the repos for the ppa you must refresh them and then upgrade packages with ```
sudo apt-get update
``` and ```
sudo apt-get upgrade
``` before trying the get_iplayer again.
Your command of **sudo get-iplayer update** would not do anything as far as I'm aware; you have to update your packages in the normal way.

---

### Post by grey1beard on 2017-04-02
Ah. Just spotted the **upgrade** has not been done. I'd run *sudo apt-get update*, but not *upgrade*

No, I'm running 14.04 on this laptop, hence having to set everything up again, but in a newer version than my old laptop.
Thanks for your help, butt I'll have to turn in now, so I'll try again Tuesday. 
Got about 600 miles of road to cover tomorrow.

---

### Post by grey1beard on 2017-04-07
Thanks for your help. All now working OK, and grabbed lots of programmes with no problems.
Regards
John

---

