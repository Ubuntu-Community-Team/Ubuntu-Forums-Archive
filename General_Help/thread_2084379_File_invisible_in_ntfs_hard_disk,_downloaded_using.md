---
title: "File invisible in ntfs hard disk, downloaded using wget."
date: 2012-11-15
forum: General Help
---

### Post by gizmoUb on 2012-11-15
i downloaded a website using wget. I stored it into ./media/s3 which is ntfs formatted partition.
When i view the directory via GUI, no such file is visible. But, when I do an  ls on the folder, I can see the name of the file that i stored ie. "www.bits-pilani.ac.in".

Please help me out! Also, is it possible to run the website from the command line? something to start the mozilla firefox browser with that file???  :confused:

---

### Post by thnewguy on 2012-11-15
Running the following command should work

firefox name-of-file.html

Keep in mind that if the file is a script, such as PHP, you won't be able to view the page directly, it would have to be interpreted by a web server.

---

### Post by gizmoUb on 2012-11-15
I worked on the problem and got what was going wrong.
I was saving the file with './media/partition3' which wasnt referring to a partition but a media file in the root folder.
But still I dont know,if next time i wanna save something on an ntfs disk, will that be error free?
Feels good to have solved it for now. Thanks for the 'firefox' cmd. :KS

---

