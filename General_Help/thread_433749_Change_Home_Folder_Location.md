---
title: "Change Home Folder Location"
date: 2007-05-05
forum: General Help
---

### Post by tylerjroach on 2007-05-05
When I made partitions a while ago and installed ubuntu i accidentally made my home folder only about 250mb and im already out of space. I dont want my home folder to be on that separate partition and is there any way i can move it to the 20gb partition ubuntu is installed on. thank you

---

### Post by hyperair on 2007-05-05
Ok here's what you do. 
1. Boot into the LiveCD, if you have
2. Go to Computer, and look for your home partition, and double click it.
3. Open another window and go to Computer, and look for the Ubuntu installation partition, and double click on it. In this window, double click on home, and double click on the folder with your username.
4. Copy all the files from the home partition into the folder you've opened in step 3.
5. Go back to the root of the drive you were accessing in step 3.
6. Double click on the folder "etc"
7. Look for a file called fstab. Right click on it and click properties. Copy the path specified by "Location:"
8. Open the run dialog (Alt+F2) and type (replace <LOCATION> with the path you copied in step 7: ```
gksu gedit <LOCATION>/fstab
```
9. Look for the line which corresponds to /home/<YOURUSRENAME>
10. Delete the entire line.
11. Save the file (Ctrl+S)
12. If you want to delete the partition and reclaim disk space you can do so using System->Administration->GNOME Partition Editor

Hope this helps.

---

