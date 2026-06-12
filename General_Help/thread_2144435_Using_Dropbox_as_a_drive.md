---
title: "Using Dropbox as a drive"
date: 2013-05-12
forum: General Help
---

### Post by chrisinleedsuk on 2013-05-12
Is it possible to map Dropbox as a drive in Linux? 

I have an android tablet (Moto Xoom 2 ME) with Quickoffice HD installed as a stock app. I can open a document from dropbox (or Google Drive, Evernote...) edit it and hit save and it saves my edit to the server. I'm sure it probably caches it somewhere but all I see as the user is dropbox being used as a drive with no manual managing of files other than hitting save in my office app. Skydrive on Windows 8 works similarly and again brilliantly with Office 2010 but not quite so well yet with dropbox (it opens but any edited documents have to be manually managed). This is great for some of my devices that have limited storage compared to my 52GB available on dropbox.

So the question is, can this be done on Linux? If so, how?

---

### Post by zero2xiii on 2013-05-12
Hay,

Not TO sure about "using it as a drive". However when you install drop box, a folder is created in your ~/ (home) directory called dropbox. All files in there are synced to your dropbox account. So essentially, I do not see the need to "Use it as a drive"? Unless I am missunderstanding the question.

Cheers

---

### Post by chrisinleedsuk on 2013-05-14
Hi,

Basically I don't want the data duplicated. The machine only has a 40GB HD and I have potentially 52GB of dropbox files. I just want to read and write from dropbox without syncing the files or managing them manually through a web browser. I tried to research how QuickOffice did it but no-one's talking ]and there's rumours that now Google have bought them it won't work soon on my tablet either :o( ]

I gather the normal way to perform this is WebDAV but dropbox don't support this themselves (I am aware of dropDAV). I was just wondering if there was a way of doing it without third party systems?

---

### Post by chrisinleedsuk on 2013-05-14
So I understand it uses dropbox's core [api]("https://www.dropbox.com/developers/core") which can be done through python etc. I might look into it this summer if I get really, really bored...

---

