---
title: "[SOLVED] Cannot access My Music nor My Images in Windows XP My Documents"
date: 2007-09-04
forum: General Help
---

### Post by jaezcurra on 2007-09-04
Hi, In a dual boot PC, I can see My Documents folder in Windows from Ubuntu, but My Music and My Images subfolders are invisible to me.  The other subfolders in My Documents are accessible 100%. TIA and best regards.

---

### Post by dragomirov on 2007-09-04
Maybe a permission thing? Try an ls -la in the folder and have a look at the response

---

### Post by jaezcurra on 2007-09-04
Nope, an ls -la of My Documents keeps showing every folder within My Documents except 2 of them: My Music and My Images :-(.

---

### Post by jaezcurra on 2007-09-04
I have been thinking of the fact that, as I am from Spain and my Windows XP is in Spanish, the name for those folders is: "Mi música" and "Mis Imágenes".  So,there are 2 accented vowels "ú" and "á".   Maybe this can lead to the problem that I am finding .  Anyone could help?

---

### Post by jaezcurra on 2007-09-04
Hi, I got it!  It was as I thought: changing the "ú" of Mi música to "u" and dealing with Mi musica makes this folder visible.  Ther is soemthing to be fixed as non English letters seem not to be recognized by the software that reads NTFS files names.

---

