---
title: "Ubuntu 13-04 Gtk noy mapping - I have no authorisation to run"
date: 2013-07-18
forum: General Help
---

### Post by Fsirett on 2013-07-18
First of all. I have viewed the threads on similar subjects and I rab "sudo Symantic"

it came up with:

(synaptic:9501): Gtk-WARNING **: GtkNotebook 0x9f28928 is mapped but visible child GtkLabel 0xa0ef678 is not mapped

(synaptic:9501): Gtk-WARNING **: GtkNotebook 0x9f28928 is mapped but visible child GtkLabel 0xa0ef730 is not mapped

(synaptic:9501): Gtk-WARNING **: GtkNotebook 0x9f28928 is mapped but visible child GtkLabel 0xa11f970 is not mapped

(synaptic:9501): Gtk-WARNING **: GtkNotebook 0x9f28928 is mapped but visible child GtkLabel 0xa0c1508 is not mapped

(synaptic:9501): Gtk-WARNING **: GtkNotebook 0x9f28928 is mapped but visible child GtkLabel 0xa0ef170 is not mapped

(synaptic:9501): Gtk-WARNING **: GtkNotebook 0x9f28928 is mapped but visible child GtkLabel 0xa0ef678 is not mapped

(synaptic:9501): Gtk-WARNING **: GtkNotebook 0x9f28928 is mapped but visible child GtkLabel 0xa0ef730 is not mapped

(synaptic:9501): Gtk-WARNING **: GtkNotebook 0x9f28928 is mapped but visible child GtkLabel 0xa11f970 is not mapped

Synaptic Package Manager also came up and sent me this message:

E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

W: Not using locking for read only lock file /var/lib/dpkg/lock

I have no idea what is going on, but I cannot save my local files and it tells me I do not have root access.

I am wondering how to fix it first, but second, I am wondering what caused it.

I do know my drive is near capacity and I suspect it probably needs repñacing quite soon- I suspect that I am going out tomorow to buy rwo new drives. One to back it all up and one to replace. In the meantime, does anybody know a quick fix?

Cheers

Frank Sirett

---

### Post by HiImTye on 2013-07-18
a few things:
-don't launch graphical apps with sudo, use gksudo instead. if you forget, then afterwards run```
sudo chown -R youruser:youruser $HOME
```make sure replace your username.
-the gtk errors are from your gtk theme, you can ignore them if you're not having display issues.
-your lock file is in use. try```
i="ubuntu-software-center|synaptic|update-manager|aptitude|apt-get|dpkg"; echo "$i" | while IFS=\| read p; do sudo killall "$p"; done; sleep 15; echo "$i" | while IFS=\| read p; do sudo killall -9 "$p"; done; sudo rm /var/lib/dpkg/lock
```

---

### Post by Fsirett on 2013-07-18
Cheers for that, I am trying them as I write. The chown command is going stright into my files for further reference. It seems to be doing its magic but I am amazed at the quantity of Thunar files it is throwint up. I suppose that is normal.

I will run the second command after the first has done its thing and see how that goes. I really need to improve my knowledge of Ubuntu but I am another refugee from Windows. I have spent a very freat deal of time having to accept what the system gives me and then, when it goes too far, simply having to collapse it all and start again. So many times Windows informed me I had a crashed drive only to find the drive was absolutely fine but there was nothing for it but to replace and reformat. This instamce is much that way in my Windows experience but now I actually have a choice!

 There certainly are a lot of Cache files in Thubar. Can I delete some of them?

Standing by,

Frank Sirett

---

### Post by Fsirett on 2013-07-18
An interesting development, possibly meaning nothing. 

While the permissions continue to change on a terminal, Libre Office decided to close while I was working and now refuses to open. It might be of some help to state that I first noticed the problem this morning when I tried to save a Libre Office file and that the two elements that i was using (and use heavily) are the sord processor and the spreadsheet programmes. I have no idea if this is a fundamental part of the problem, a symptom of the problem or an indicator that may help in the diagnosis. 

I note here that Firefox seems to be operating normally and that the terminal is (still?) changing ownership of my Thunar cache sessions and is showing little sign of stopping. 

I have no idea of what is going on, but I just wanted to add events as they happen to aid the kind souls who are offeringtheir help and to help guide others with the problem to this solution when it comes

F.S.

---

### Post by Fsirett on 2013-07-18
The first line of code (the Chown) has completed and seems to be all okay (as far as I know).

However, Firefox has now disappeared and does not open. therefore I am using my wife's (acursed!) laptop to continue. 

I typed in the second line of code ( the unlock code) and get this response:
"
bash:syntax error near unexpected token 'done'

I have been th centre instead of center and a couple of /rough the code and I did have a couple of errors: "centre" and "/"; but I seem to have all of the spaces and thee punctuation the same.

I thought maybe a final semicolon was absent and tried running it with that added but it remained obstinate.

Sorry to be such a pain, but is there something I am missing?

It all seemed to be going so well.

Cheers

Frank Sirett

---

### Post by Fsirett on 2013-07-18
i restrted the computer in complete frustration.

I did not send screenshot of my terminal because I had no access to the internet and could not save anything.

I opened in safety (?) mode.and repaired all packages, freed some space and had the files checked. I have just restarted.

fingers crossed, but more likely wires!
   
Up and running but when my Firefox wanted to restore and had problems, it had about a week of tabs it was trying to open. I suspect that might be a part of the original problem.

Tomorrow, I buy a new disk and I back everything to do with the system on to that and have a rebuild of the disks. Maybe two disks so I can reload onto a fresh disk and hope the old one is not crashing instead of relying on it.

My computer id in its sixth or seventh year, so I suppose it might be showing its age as well. It gets a lot of usage and there could be some breakdown.

In any case, thanks for your help, you are a champ and I hope this will help bail someone else who staggers down my path

Frank Sirett

---

