---
title: "uploading some files in ubuntu"
date: 2013-06-02
forum: General Help
---

### Post by babakflame on 2013-06-02
Dear Buddies
Hi

I want to upload some files in ubuntu. would some body plz hint me how can I do it?:confused:
   Regards
    Bobi

---

### Post by Cheesemill on 2013-06-02
Upload files to where?

---

### Post by gordintoronto on 2013-06-02
+1

The procedure is determined by the recipient. For example, I can upload a file to Dropbox by dropping the file into my Dropbox folder. To upload to my web site, I use ftp, which is completely different.

---

### Post by babakflame on 2013-06-03
Dear Buddies
Hi

Let me make it clearer. I want to upload some files so some one else can download it by internet. I have downloaded some files from github; So I think I can use this site. Although I have made an account there, still I do not know how can I put my files there; so specified persons can download it:confused:
   Regards
     Bobi

---

### Post by Lars Noodén on 2013-06-03
You'll need to have a machine that has a publicly available ip address or hostname.  Then you'll also have to have either a web server or an SFTP server or a torrent, depending on how public you want your files to be.  Do you want your files available to anyone that finds them or just to people with the right username and password?

---

### Post by deadflowr on 2013-06-03
> **babakflame said:**
> Dear Buddies
Hi

Let me make it clearer. I want to upload some files so some one else can download it by internet. I have downloaded some files from github; So I think I can use this site. Although I have made an account there, still I do not know how can I put my files there; so specified persons can download it:confused:
   Regards
     Bobi

You'll need to create a new repo on github

Assuming you've already set up git
[https://help.github.com/articles/set-up-git](https://help.github.com/articles/set-up-git)

Then follow this one to make a repo
[https://help.github.com/articles/create-a-repo](https://help.github.com/articles/create-a-repo)

---

### Post by gordintoronto on 2013-06-03
Easier than that, would be to get a free Dropbox account, and upload into your "public" folder on Dropbox. You can then get a link to send to anybody you want to make the file available to.

I'm pretty sure there is a similar procedure with Ubuntu One.

You might need to do some reading, do your own research.

---

### Post by babakflame on 2013-06-05
Dear Buddies
Hi
Thanks for your hints. I have started with  Github. At the moment I have created a repository there. However, Now my problem is that how can I put my files in that repository?
  I have investigated Github site but I did not find anything maybe I am too brandnew with this issue:confused::confused::(
   Regards
    Bobi

---

### Post by Cheesemill on 2013-06-05
What sort of files do you want to upload?

Github is designed for sharing the source-code for computer programs, if it is something else that you want to share then you would be better off using a file-hosting service such as [File Dropper]("http://www.filedropper.com/"), [Sendspace]("http://www.sendspace.com/") or [Dropbox]("https://www.dropbox.com").

---

### Post by babakflame on 2013-06-06
[INDENT]Hi Cheesemill
I am exactly going to share a computer source code through github :), Is there any body who can help me on required codes for uploading my files through github?:(

  Regards
   bobi

[/INDENT]

---

### Post by Cheesemill on 2013-06-06
Have you read the documentation?

[https://help.github.com/articles/set-up-git](https://help.github.com/articles/set-up-git)

---

### Post by babakflame on 2013-06-06
Hi Cheesemill
I did exactly as it said in this link. I put my file which contains the code there. Then I tried to make a README file and in first step upload README and then the code file.
In the last directive for README I got this error:

```
babak@babak-VPCEA26FG:~/Large_Eddy$ git push origin master

Username: 
Password: 
error: The requested URL returned error: 403 while accessing https://github.com/
```

Would somebody PLZ help me hat is error 403 and how can I get rid of it?

  Regards
   Bobi

---

### Post by babakflame on 2013-06-07
Dear Buddies
Hi
I have find the solutions for error 403 and first I should check my git version. After typing the required directive for updating my git version from 1.7.5.4 to 1.7.10.:
```
git clone https://github.com/git/git.git
```
My result is this error:

```
fatal: destination path 'git' already exists and is not an empty directory.
```
Would somebody PLZ hint me how can I solve this error?:(:confused::confused:

Regards
  Bobi

---

### Post by babakflame on 2013-06-08
Dear Buddies
Hi
Since I have got no response about my problem. ](*,) I think its better for me to start a new thread with the exact problem with Git. Would somebody PLZ hint me that in which category should I create the thread?](*,)
  Regards
   Bobi

---

