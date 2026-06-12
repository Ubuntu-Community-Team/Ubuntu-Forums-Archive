---
title: "Sharing Limited Firefox Profile in XP/Ubuntu Dual Boot"
date: 2007-06-16
forum: General Help
---

### Post by Brerlapn on 2007-06-16
I am having trouble using symlinks with Firefox and am hoping someone else will be able to point me at the precise place the process is breaking down.

I have a Fat32 partition mounted from a shared partition.  My XP Firefox and TB profiles are both aimed at that partition.  I want to get my Ubuntu Firefox to also point at that profile, and have tried both the profilemanager and hand-edited the profile.ini file to point at the shared partition.  The profile is loading (I can see my bookmarks and my extensions) but the Ubuntu Firefox isn't running extensions correctly and won't open preferences dialogue boxes for the extensions, which leads me to believe something is breaking when my Ubuntu-side Firefox tries to use that profile.

Since all I really want is to have the same bookmarks, saved passwords, and extensions on both sides of the dual boot, I tried created a symlink from the default profile in Ubuntu (so that Firefox would run correctly) just to the bookmarks.html file in the shared partition.  (I read here or elsewhere that hard links don't work across different filesystems, hence the symlink.)  The symlink shows up in the Ubuntu default profile folder just fine, but when I open Firefox, I get no bookmarks at all, like it is unable to pull the data through the symlink file from the shared partition.

The only thing I can think of is that maybe there is a weird permissions issue due to pulling the data from another partition, but I am not seeing any error messages anywhere.

For further background, the shared partition is a truecrypt canister.  I worked out all the kinks with permissions and read/write, and it functions without problem in all other respects, so I don't think that is the source of the problem.  I would expect the same issue whether the Fat32 is just another drive partition or the truecrypt canister.  I use the canister for security in case my laptop gets stolen (all sensitive info resides there), so I am really hoping someone can help me figure out how to selectively use that firefox profile.  Once I figure out how to do bookmarks.html, I will also symlink to the saved passwords file, my extensions folder, and my cache folder.

Thanks in advance.

---

### Post by Brerlapn on 2007-06-17
For reference of anyone else having a similar problem, I was able to get the symlinks working.  Based on instructions at [this link]("http://http://tinyurl.com/2ql2xv") in response to a similar problem, I decided to try installing Konqueror (the KDE file manager) to see if it would be able to successfully be able to create symlinks.

Using Konqueror, I was able to create a symlink to my bookmarks and signons files, as well as my cache, searchengines, and extensions folders from the profile of my Ubuntu Firefox installation to the Windows profile in the encrypted canister.

I had previously tried creating the symlinks manually in a terminal window, and graphically using the Gnome file manager, but neither worked.

I don't know why Konqueror was able to create useable symlinks when the other methods wouldn't, but if you are having problems with symlinks in 7.04, it would be worth it to see if Konqueror is able to create them.

---

