---
title: "Firefox fails in Lx after moving its profile onto an NTFS volume for dual boot"
date: 2014-05-28
forum: General Help
---

### Post by Cbhihe on 2014-05-28
On ar dual boot machine, Firefox does not run under Lx with a profile on a shared NTFS volume.
The error message is: "Your Firefox profile cannot be loaded. It may be missing or inaccessible."
--
Prior to that I had moved the Firefox profile to its new location on the  NTFS C. volume, In doing so I also had to modify my  ~/.mozilla/firefox/profiles.ini file as follows:
[B]
BEFORE[/B] (as automatically generated)

[General]
StartWithLastProfile=1
[Profile0]
 Name=default
 IsRelative=1
 Path=a59yph8k.default
# eof

**AFTER** (modification)
[General]
StartWithLastProfile=1
[Profile0]
Name=default-1401050540678
IsRelative=0
Path=/media/lxuser1/Win-xp/'Documents and  Settings'/winuser1/'Application  data'/Mozilla/Firefox/Profiles/agn2j40h.default-1401050540678
# Path=/media/lxuser1/Win-xp/Documents\ and\  Settings/winuser1/Application\  data/Mozilla/Firefox/Profiles/agn2j40h.default-1401050540678
# eof

The folder agn2j40h.default-1401050540678 was automatically created by Fx on an NTFS partition under Win xp at: 
C:\Documents and Settings/winuser1/Datos de programa/Mozilla/Firefox/Profiles/agn2j40h.default-1401050540678

I tried to write the above path in 2 ways to make it understandable to Lx.
The   C:   volume under Win-xp becomes the mount point    /media/user1/Win-xp    under Lx.
Then there is the problem of spaces in long Win names. 
   - In one case I  escaped them with \ as in   Application\ data   , 
   - In the other one I single-quoted the folder name as  in 'Application data'. 
Both seem to work in command line. I thought it might also work in the  profiles.ini file under Lx. Apparently not, since Fx cannot find its  profile under those condtions. 

Is something wrong with my syntax or something else ? Can anybody help ?
Cheers,

-ced

---

### Post by matt_symes on 2014-05-28
Hi

I've never tried what you are attempting to do but my initial thoughts would be permissions.

They get stripped of on an NTFS volume and fx may be relying on them under linux. I would investigate that first.

But even then, i would question whether this is the way to go. You may get issues if ine version of fx is more up ti date than the other.

I would look into the sync functionality of fx and see if that solves your needs.

Kind regards

---

### Post by Impavidus on 2014-05-28
There are some experienced users who share their firefox profile between Win and Ubuntu in that way, so it cannot be too bad. Or can it?

First, the obvious, is that directory called "Application data" or "Datos de programa"? It has to match of course.

I think both the quote style and the escape style should work. I would put the entire path in a single set of quotes, like```
Path='/media/lxuser1/Win-xp/Documents and Settings/winuser1/Application data/Mozilla/Firefox/Profiles/agn2j40h.default-1401050540678'
```

Now the most likely cause of the error. Is the Windows partition automatically mounted? If it's not automatically mounted you have to manually mount the windows partition at that location (by clicking it in the file manager) before you can start firefox. /media/lxuser1/Win-xp seems the path where the file manager would mount that partition. It may be easier if you configure your system to mount that partition automatically using fstab.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Cbhihe on 2014-05-28
Thanks matt_symes.
> **matt_symes said:**
> 
.... my initial thoughts would be permissions.
They get stripped of on an NTFS volume and fx may be relying on them under linux. I would investigate that first.
To the best of my knowledge it is not the case. The fact I have application data files on an NTFS just makes it accessible to all when the system is Win-xp booted. T'is all. Lx does not give a hood. 
> **matt_symes said:**
> 
You may get issues if the version of Fx is more up to date than the other. 
No issues whatsoeer except for the occasional addon incompatibility under either Win-xp or Lx. a few addons are OS specific after compilaition, in the sense that their binaries differ. It is the case of Lightning for Tb. For me it is a minor issue and there are work-around solutions in posted threads in Tb / Lightning's case.
In fact I first read then heard from a Forum's moderator (was it oldfred ? ) that platform-specific compilations of Fx can run well, while sharing data betwwen Lx (64bit) and Win (32 or 64bit). Not just differences in builds but also in versions seemed to bear no consequence when sharing data across boot env boundaries. I suppose it cannot be not true of all versions - so I'd take this with a grain of salt - but that gives an idea of the upward-downward compatibility of the Fx engine when it comes to sharing profiles files between boot-env.  
> **matt_symes said:**
> 
I would look into the sync functionality of fx and see if that solves your needs.
I did give time to the idea of using the sync feature already weeks ago, but it is not the right solution for me.  I have real qualms about using cloud-based storage, _**any**_ cloud based storage. The crux of the matter is: why use cloud-storage, as it compromises your security and incidentally increase your carbon footprint, when **there has to be** a local solution at client level ? ;) 

-ced

---

### Post by Cbhihe on 2014-05-28
Thanks Impavidus.
> **Impavidus said:**
> There are some experienced users who share their firefox profile between Win and Ubuntu in that way, so it cannot be too bad. Or can it?
You're right, it cannot be that bad. I already posted a more general question on the topic  of displacing the Fx and Tb profile for them to be shared between two  boot-env. 
As an absolute begineer, I got assistance from **oldfred** and  **sudodus** (see for instance  [http://ubuntuforums.org/showthread.php?t=2223124](http://ubuntuforums.org/showthread.php?t=2223124)).

At that time, I  wanted the shared files for both Tb and Fx to be located somewhere in  /home (D:\), a partition on my internal HD with ext3 format.
For  read-write compatibility from Windoze, I used ext2Fsd. Problem ? Yes, big time ! My  CPU usage shot up to 100% under Win xp and my 
worstation ground to a halt  almost instantly when ext3 volume read-write accesses were controlled by Win apps.  
      [I]Opening one message in Tb becomes an opportunity to visit the bathroom or the coffee machine and loading any page in Fx
      a good opportunity to have lunch. [/I]
When plain and simple using Windows Explorer however, there is no problem; all ext3 volume have volume labels and are read-write compatible. 
Conclusion: don't use Ext2Fsd other than to make rwx access from Win Explorer possible.
So  I transfered profiles back somewhere onto C:\ (NTFS) and now look at accessing  profile located on NTFS from Lx. It's the inverse problem.

BTW, I did read the thread started by **rbmoler** on 2014.03.16 ([http://ubuntuforums.org/showthread.php?t=2211562](http://ubuntuforums.org/showthread.php?t=2211562)) and saw that his/her issue and yr contribution 
are well related to my trouble.
> **Impavidus said:**
>  ... is that directory called "Application data" or "Datos de programa"? It has to match of course.
Yes, they do match. It is just that I did not translate the Spanish terminology used on my OS thoroughly enough,
 
> **Impavidus said:**
> I think both the quote style and the escape style should work. I would put the entire path in a single set of quotes, like
```
Path='/media/lxuser1/Win-xp/Documents and Settings/winuser1/Application data/Mozilla/Firefox/Profiles/agn2j40h.default-1401050540678'
```
Will do. Wndoze "holy" names are a real pain in the __. Coming from Unix, I always looked at them with incredulity... Now they strike back.

> **Impavidus said:**
>  Now the most likely cause of the error. Is the Windows partition automatically mounted? If it's not automatically mounted you have to manually mount the windows partition at that location (by clicking it in the file manager) before you can start firefox. /media/lxuser1/Win-xp seems the path where the file manager would mount that partition. It may be easier if you configure your system to mount that partition automatically using fstab.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
Until I read rbmoler's thread and your posts, I had the feeling that, yes, they were mounted because I saw them the Win-xp icon in my launch bar, something that cannot happen un my normal work env in Unix. But now that you mention it. I remember something odd from last night. I was working in command mode and worked with sed scripts across volumes. I tried to access /media/lxuser1/Win-xp and my script return errors that showed me that it could not access certain files on that volume. I was intrigued and whent into X-window mode (or whatever it is called under Lx) and double clicked on the corresponding file tree, eventually finding the file and opening it. I rerun the script and this time it worked. (??!)  I thought it was a glitch and did not try to repeat the behavior because it was real late. Now I think that it might have been a stupid mount problem.
I will look at fstab to see if it differs from what I already know, but if you have a ready solution, I'll take it.

Do you guys think I should spend 6 months in Tibet without eating in order to cleanse myself from Windoze's corrupting influence ? :D 

-ced.

---

### Post by Cbhihe on 2014-06-03
[FONT=garamond][SOLVED]

[SIZE=2]The correct way of writing the path is (after proper editing of my [FONT=courier new]/etc/fstab[/FONT]):[/SIZE]
[/FONT][FONT=garamond][FONT=courier new]Path=/mnt/Win-xp/Documents and Settings/[winuser1]/Application data/Mozilla/Firefox/Profiles/xxxxxxxxx.default[/FONT]

where[FONT=courier new] /mnt/Win-xp[/FONT] is the automatic mount points for the NTFS volume [FONT=courier new]C:\[/FONT] . 
In other words there are no backslashes to escape spaces in "holy" names or single quotes or anything. Just write out 
the path with names containing spaces as one would in Windows.
Remember to configure the mounting of C.\ at startup by default.

-ced. 
[/FONT]

---

