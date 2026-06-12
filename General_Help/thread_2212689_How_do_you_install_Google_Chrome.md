---
title: "How do you install Google Chrome?"
date: 2014-03-22
forum: General Help
---

### Post by DorelXD on 2014-03-22
Guys, I am desperate! How can you install Google Chrome? No matter what I do I get the error:

```
Errors were encountered while processing:
 google-chrome-stable:i386


```

I searched the internet for a possible solution and tried to run sudo apt-get -f update, but it didn't work. Could somebody please help me?

---

### Post by Korkel on 2014-03-22
Save [this]("https://www.dropbox.com/s/7kmari1rhgy4j8w/google-chrome-stable_current_amd64.deb") file to the same file as [this]("https://www.dropbox.com/s/0ui58uhc80whiel/Chrome-setup.sh") file. Run the second downloaded file in a terminal, it will install Google Chrome.
[B]
[s]Edit: It is a Dutch script, will make a English version.[/s]
Edit 2: English version added.[/B]

---

### Post by bug67 on 2014-03-22
Sourced from [here]("http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/").  This will install a PPA so Chrome will always be the latest version.

1.  Install the signing key and enter password when prompted:
```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
```

2.  Add it to the repository:
```
sudo sh -c 'echo "deb http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list'
```

3.  Update
```
sudo apt-get update
```

4.  Install stable version of Google Chrome:
```
sudo apt-get install google-chrome-stable
```

---

### Post by DorelXD on 2014-03-23
Thank you both for your help!

@Korkel, I didn't try your solution first because I thought it was a 64-bit version and I have a 32-bit system. I thought that because of the "amd64" in the name of the file

@bug67, worked like a charm! Thank you very much!!!

---

### Post by deadflowr on 2014-03-23
> I didn't try your solution first because I thought it was a 64-bit  version and I have a 32-bit system. I thought that because of the  "amd64" in the name of the file

And you would be right.
Haven't done this myself, but I would expect even more damning errors from trying to install the 64-bit package then what you were getting from the 32-bit package.

---

### Post by DorelXD on 2014-03-23
> **deadflowr said:**
> And you would be right.
Haven't done this myself, but I would expect even more damning errors from trying to install the 64-bit package then what you were getting from the 32-bit package.
Hmmm, so I was right. Well, I'm quite a noob, but I want to learn!

---

### Post by bug67 on 2014-03-23
> **DorelXD said:**
> Thank you both for your help!

@Korkel, I didn't try your solution first because I thought it was a 64-bit version and I have a 32-bit system. I thought that because of the "amd64" in the name of the file

@bug67, worked like a charm! Thank you very much!!!

Awesome!  Glad you got it.  Consider clicking on the "Thread Tools" link and marking as "solved" so that others looking for help will know this was a good answer.  :)

---

