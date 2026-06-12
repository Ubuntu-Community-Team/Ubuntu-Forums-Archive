---
title: "File corruption?"
date: 2008-03-15
forum: General Help
---

### Post by uberlube on 2008-03-15
I recently installed linux on a friends laptop, who has 2 HD within. Windows was snug in its own partition and I installed Linux Mint on the other. On his Win, I transfered some .avi format movies into his /home folder and he called me today to complain that he lost the audio in half of them. Is this a common problem, or is this just a once in a blue moon kinda thing? If the latter, then does this mean that the NTFS write to EXT3 is still buggy and needs work still?

---

### Post by Thanoulis on 2008-03-15
I didn't quite understand the situation...
Let's say you copy some divx files from the NTFS to Ext3, ok?
And let's also say that these files when played from the Linux applications (say Totem player) do not have sound...
Then there are 2 things happening:  
1) The NTFS to Ext3 copy is buggy (i do not know about this, i do not use windows for a long time now),
2) The Linux codecs are not ok, or not installed, or something (mine work fine, though).

Did you try to play these files in win32, or just in Linux? And if you tried, did you try with different players? (VLC, Mplayer, Totem)

---

