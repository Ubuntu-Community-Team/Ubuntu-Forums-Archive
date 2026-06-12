---
title: "Monodevelop with Edgy = security problem?"
date: 2006-11-02
forum: General Help
---

### Post by ScottMorris on 2006-11-02
Yesterday I installed a fresh Edgy and now when I try to build a file in Monodevelop and I get the error

>  Building Project: csvread Configuration: Debug

Build failed. Can't create project output directory /bin/Debug original exception:
System.UnauthorizedAccessException: Access to the path "/bin/Debug" is denied.
  at System.IO.Directory.CreateDirectoriesInternal (System.String path) [0x00000] 
  at System.IO.Directory.CreateDirectory (System.String path) [0x00000] 
  at System.IO.DirectoryInfo.Create () [0x00000] 
  at (wrapper remoting-invoke-with-check) System.IO.DirectoryInfo:Create ()
  at MonoDevelop.Projects.Project.DoPreBuild (IProgressMonitor monitor) [0x00000] 

what do I need to do to get this to work as it did in Dapper?

---

### Post by ScottMorris on 2006-11-02
I'm guessing that it has something to either do with the security settings of Ubuntu or of MD, it never used to do this and i have chmoded the permissions on the folder and files that I'm accessing.  This is confusing.:???:

---

### Post by po0f on 2006-11-02
ScottMorris,

Are you trying to build your programs directly into /bin?  That is a little dangerous.  You shouldn't change the permissions on this folder to get write-access either, it's write-protected for a reason.

---

### Post by ScottMorris on 2006-11-02
I didn't touch that folder, good thing to.  The old version built the files into a structure of *current folder*/bin/.... and re looking at the message it was trying to put them into the /bin not **/bin.  do you know how I may go about changing the build point?

---

### Post by po0f on 2006-11-02
ScottMorris,

I've never used MonoDevelop, but try looking through the project options or build options.

---

### Post by ScottMorris on 2006-11-02
There is not option in the Preferences to change its output dir so I want searching through its program files, besides learning that MonoDevelop is made using Mono I couldn't find the output dir their either.  If anyone knows how to configure this in Monodevelop please help.

---

### Post by ScottMorris on 2006-11-03
More infomation is that I'm using it to work on single files, I can change the build dir when I create a solution, but thats not what I'm doing.  0.10 just created the /bin/Debug in the working dir of the file but 0.12 is trying to make it in the actual location on root (bad).  If anyone knows how to change this to ./bi... it would be greatly apreciated

---

### Post by digby280 on 2006-12-07
> **ScottMorris said:**
> Yesterday I installed a fresh Edgy and now when I try to build a file in Monodevelop and I get the error



what do I need to do to get this to work as it did in Dapper?

Hi Scott,

I had the same problem.  I resolved it by creating a project first and then creating a class inside that project.  In much the same way as you do in Netbeans.

Hope this helps.

---

### Post by ScottMorris on 2006-12-09
Thanks.  That had crossed my mind but as it seemed to cause some problems I installed Xubuntu 6.06 an a small partition and am using it there.  So far that is working nicely. :)

---

