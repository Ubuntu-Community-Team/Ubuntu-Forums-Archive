---
title: "&quot;permission denied&quot; when running a script as root user"
date: 2020-05-22
forum: General Help
---

### Post by pigswipe on 2020-05-22
As a root user, i ran a script that tries to access a folder which is from a different user, and it tells me that i dont have permission. How do i make it so i can run the script at the directory?

---

### Post by GhX6GZMB on 2020-05-22
What exactly do you mean with the phrase "as a root user"?
There's no such thing in Ubuntu. You can temporarily elevate your access rights for a command using sudo, that's all.

---

### Post by yancek on 2020-05-22
Did you make the script executable as if it is not, it will produce that output.

---

### Post by Impavidus on 2020-05-23
Where does the "permission denied" error come from? Is it because your script cannot access the file or directory it's targeted at, or is it because you have (your root has) no permission to run the script? The precise error message may help.

---

