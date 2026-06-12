---
title: "how to open a forwarded email (.eml format)"
date: 2005-07-01
forum: General Help
---

### Post by arnieboy on 2005-07-01
This is a question I have been asking for 4 years and I still havent got any reply. 
How do I open a forwarded email in **.eml format** on linux? 
For example when i get a forward from my friends and open it in any mail client (like thunderbird) and double click on the .eml attachment, it just keeps opening the same page over and over again (as many times as I double click) and never manages to retrieve the real file embedded in the email attachment. 
I badly need help on this one.
Thanks in advance.

I am sure lots of other thunderbird and evolution users have faced the same problem. 
It would be nice if atleast people acknowledge that this problem indeed exists or have I missed something?
I can cite one example: if u forward anything from your yahoo mail account it will be forwarded in .eml format. I have never been able to open these forwards from yahoo accounts on linux (on any mail client).

---

### Post by arnieboy on 2005-07-03
bump! ](*,)

---

### Post by tread on 2005-07-03
Just save it and then open it using gedit .. that should work. As far as I know, and eml format isn't a binary format, so you can read the email, though mime attachments wont make much sense at the end of the email.

---

### Post by arnieboy on 2005-07-03
if i open it in gedit, it will be give me a bunch of gibberish.. I need to extract the forwarded file embedded in that .eml file rather than read the eml file in a text editor. In outlook on windows, if u double click on the mail, it will keep opening the layers (of senders sending the mail to others), till it reaches the actual file and then u can view it. Isn't there any such functionality on linux to do this (directly or indirectly)?

On linux mail clients (like thunderbird), the first layer opens successfully (wherein u see who forwarded the email to the person who has sent it to u in turn). But after that, it keeps opening the same window over and over again, failing to read the inner MIME layers.

---

### Post by arnieboy on 2005-07-04
bump! ](*,)

---

### Post by nocturn on 2005-07-04
I think abiword can handle them.

Good luck

---

### Post by arnieboy on 2005-07-04
no it cant! just tried! abiword has a .eml exporter plugin but no .eml importer plugin :( bump ](*,)

---

### Post by LxP on 2006-11-21
I would also like to do this.  I believe I've had success with KMail in the past, but after downloading and installing it just now I cannot open a .eml file I saved using Mutt.

Does anyone have any more thoughts on this after the year of silence?

---

### Post by 8rdx on 2007-03-04
I just ran into this problem w/yahoo and it took me a while to figure it out...

1) Open the attachment in gedit.
2) Scroll down to the "From:" line and copy it.
3) Paste the "From:" line at the very top.
4) Remove the ":" (colon).
5) Save.
6) Drop it back into Evolution.

It SHOULD work. At least it did for me.

If HTML mail looks silly, you may need to allow images:
Edit>Preferences>Mail Preferences>HTML Mail>Load Images
"Always load images from the internet"

Hope this helps! :)

---

### Post by jimbob on 2007-03-05
Here is a way to do it using Thunderbird.  I know it isn't pretty but it works. The method involves converting it to mbox format and then moving it into T-bird in a special inbox of your choice.

1)  apt-get install ruby
2)  from the URL:  [www.broobles.com/eml2mbox](www.broobles.com/eml2mbox)  download and unzip eml2mbox.zip into your home account
3)  create a receiver directory in your account, call it my_emls or something
4)  move one or more of your saved  *.eml's into this directory
5)  in T-bird create a folder under Local Folders, call it Inboxmbox
6)  run the following command in your account:
        ruby eml2mbox.rb ./my_emls /home/<your account>/.mozilla-thunderbird/xxxxxxx.default/
             Mail/"Local Folders"/Inboxmbox

       (you will have to find the value of xxxxxxx by looking under .mozilla-thunderbird)

Notes:  for some reason you must fully qualify the last argument or it can't find the file.
              you must completely clean out the my_emls folder each time or ALL the entries will be      put in again.
              you will be given the choice to (o)verwrite, (a)ppend or (c)ancel on the Inboxmbox folder.

I am working on a script to perform the conversion and move as the command is so darn long to type in each time.
For some reason I am getting more and more of these .eml attachments than ever before.  If anyone else has noticed this please let me know.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by richardh9936 on 2007-06-06
My MS friends are generating messages with .eml extensions.  The worst ones are those that (a) contain attachments and (b) that they received from other MS users and (c) that they forward as an attachment.

The fastest way around is to give them a gmail account.
Richard.:mad:

---

### Post by pounentesWind on 2007-11-07
Can someone explain what the xxxxxxx.default is?and how can one see its value?
seems it is a problem to read eml.files in linux...

---

### Post by jimbob on 2007-11-09
See step #6 in my post above.  Look in your home directory under /home/<your login>/.mozilla-thunderbird  and you will see a strange file with a name like joyo3nbg.default - this is the one created by T-bird to store your mail stuff in.

---

### Post by Icarosaurus on 2007-11-16
It seems my version of Evolution (2.1.2.1) can handle an .eml attachment without problems... I have a forwarded mail with some pictures and i visualize it by clicking on the attachment button...

---

### Post by alex_goodwin on 2007-11-28
I've run into the same problem today. After googling for some time I found out that:
> kmhtConvert is an mht (Microsoft Windows (R) Web Archive) file to war (KDE Web Archive) file converter. Since version 0.7 kmhtConvert is able to open and display MHTML and EML (Microsoft Windows (R) Email Archive) files.
So, that could be a solution, at least for kubuntu.

---

### Post by magoraf on 2008-05-14
I found this method to open .eml files in Ubuntu with thunderbird :

 - right click on the file -> open with -> open with other applications...
 - open the textfield cliking on "use a custom command" and type : "thunderbird %f" and then click on Open button.

Since this moment simply double cliking on every .eml file, it will be opened with thunderbird correctly.

---

### Post by jimbob on 2008-05-14
This does not work for me.  I do not get a field that says "use a custom command" - all I get is a list of files in my home directory along with the standard devices and places list in the left column.

---

### Post by jvin248 on 2008-05-16
I just tried with some .eml files sent to me (Xubuntu 7.10) - they were packaged in .rar file (which I was able to open), first offered Abi-word (gibberish file), then tried the "open other" and put in "thunderbird %f" and never heard from that launcher again, though the next time I tried it the open other option had the "thunderbird %f" command in its history list.

Did magoraf have a thunderbird extension that we don't?  Or working with 8.04 (I'm on 7.10)?

---

### Post by jvin248 on 2008-05-16
I found and tried this Thunderbird extension:

[http://nic-nac-project.de/~kaosmos/mboximport-en.html](http://nic-nac-project.de/~kaosmos/mboximport-en.html)
[http://tech.niques.info/thunderbird-import-eml/](http://tech.niques.info/thunderbird-import-eml/)

Seems to work as far as Thunderbird says "Eml files importing:1" but it never shows up either!  Is it supposed to spawn another window, save the file somewhere, or just hangs?

Xubuntu 7.10
Thunderbird 2.0

J

---

### Post by jimbob on 2008-05-21
My post, #10 above (although cumbersome to set up initially) still works quite well.  Has anyone bothered to try it?

---

### Post by fi11222 on 2008-05-28
Hi Jimbob. It worked for me. I just tried it. Thanks.

---

### Post by phxrider on 2008-07-10
[LIST=1][*]save the eml file
[*]go into Evolution
[*]create new message
[*]attach the eml file (Gmail/Firefox will save it without the .eml extension, this is fine since Evolution does not need the extension to figure out what the file is)
[*]save the message as a draft
[*]open the draft and where you see the attached file, there will be an option to view inline, choose that and you will see the attached .eml as it would appear in Outlook/Outlook Express.[/LIST]

There might be an easier way to get to the same end result, but I don't know Evolution very well.

---

