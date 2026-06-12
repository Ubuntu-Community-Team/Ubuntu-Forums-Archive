---
title: "[SOLVED] How can I determine the file path to T-Bird mail?"
date: 2007-11-08
forum: General Help
---

### Post by discmaster on 2007-11-08
How can I determine the file path to T-Bird mail? 

My T-Bird mail will not open when I click on an email in a webpage. It was fine until a FF update about a week ago, I think...

Thanks

---

### Post by kebes on 2007-11-08
In a terminal, you can type:
```
which mozilla-thunderbird
```
And it will tell you the path for that binary. The default path should be:

/usr/bin/mozilla-thunderbird

---

### Post by discmaster on 2007-11-08
Can anyone confirm that this looks right?

> home/tr/.mozilla-thunderbird

I put this in following the instructions for setting up the mail, & it didn't fix anything :(

This is the instructions I have;
> These steps will allow opening your desired email client in Linux when operating in Firefox and using its menus, or when activating an email link on a Firefox page:

   1. In Firefox's Location (URL) Bar, enter "about:config" and then press <enter> or click "Go".
   2. With the cursor in the body of the resulting page, <right-click> the mouse.
   3. From the pop-up menu, select "New".
   4. From the next pop-up menu, select "String".
   5. In the pop-up dialog box "Enter preference name", enter "network.protocol-handler.app.mailto" (without quotes), and click "OK" (You might wish to cut-and-paste that phrase to ensure correct spelling).
   6. In the pop-up dialog box "? network.protocol-handler.app.mailto", enter "/usr/bin/kmail" without quotes [or the actual filesystem location of your desired email client] and click "OK". This should be the Full Path of the program, i.e. "/usr/bin/kmail", not just the path "/usr/bin". 

Without restarting Firefox, you can test by opening or switching to another tab. from the Firefox top menu select, "File -> Send Link". Your desired email client should open.

        If that doesn't happen, redo your steps, ensuring the spelling of your entries is correct, and ensure the actual Full Path of your desired mail client is entered. 



**Help? **   :popcorn:

---

### Post by discmaster on 2007-11-08
> which mozilla-thunderbirdI put that in a term, hit enter & it didn't tell me anything? :confused:

---

### Post by KrazyPenguin on 2007-11-08
Try:

which thunderbird

because it is installed under thunderbird in /home and not mozilla-thunderbird

and it seems you have the answer to your problem with the solution you posted, unless you are having trouble with it.

;-)

---

### Post by kebes on 2007-11-08
> **discmaster said:**
> I put that in a term, hit enter & it didn't tell me anything? :confused:

Do you have thunderbird installed? Did you install it via Synaptic, or manually?

Maybe try:
```
apropos thunderbird
```
...and see if it lists anything. If it does list something (maybe "thunderbird" or whatever) then go:
```
which thunderbird
```
(or whatever)

If you installed it manually, but can't remember where you put the binaries, you can also try:
```
locate thunderbird
```
... to help find it.

---

### Post by discmaster on 2007-11-08
> which thunderbird

because it is installed under thunderbird in /home and not mozilla-thunderbird

and it seems you have the answer to your problem with the solution you posted, unless you are having trouble with it.Well, that looks like that fixed it; I was looking manually for mozilla-thunderbird, & **I found that in my Home folder, so what is that?**

**Also, I would like to know; What broke it in the first place?** The onlu update I know of that I did to FF was an update for a theme that I have installed. 

Thanks for your help, you guys know all the answers!!! :popcorn:

---

