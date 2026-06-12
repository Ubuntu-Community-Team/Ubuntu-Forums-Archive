---
title: "Encrypting file fails In Evolution"
date: 2020-12-30
forum: General Help
---

### Post by wildmanne39 on 2020-12-30
I need to encrypt a file and send it using evolution if possible but it keeps failing with the following error:
> Could not save to autosave file &#8220;.evolution-composer.autosave-C27IW0&#8221;.

Error saving to autosave because &#8220;Failed to encrypt: Invalid recipient  36b683899ee341aaa02d2a573cbc398a specified. A common issue is that the gpg doesn&#8217;t have imported public key for this recipient.&#8221;.
I have the recipients gpg key imported, it is in seahorse and I checked also in the terminal with:
```
gpg --list-keys
``` 
and it is present, I understand evolution can be a pain sometimes, it is my understanding there are two different files that the gpg key may be stored in and it may be trying to retrieve the information from the wrong file, I tried for several hours last night to get the file sent, if there is a easier, better way please advise I really do not care I just want to get it done as quickly and easily as possible because I have other more pressing matters to attend too, I did find a command to encrypt and email the file from the terminal but I never got it to work:
```
gpg --encrypt --sign --armor -r mary-geek@protonmail.com
```
from what I can tell --armor -r is no longer a command in Ubuntu, all thoughts and help is very much appreciated.

Thanks

---

### Post by #&amp;thj^% on 2020-12-30
This really can be a very huge pain not to mention inconvenient with evo, see if this will work for you: [https://support.docusign.com/en/articles/How-do-I-sign-a-DocuSign-document-Basic-Signing](https://support.docusign.com/en/articles/How-do-I-sign-a-DocuSign-document-Basic-Signing)

---

### Post by wildmanne39 on 2020-12-30
That does look a lot easier, I have esigned documents for my loans but that is it, I do not think users in the Ubuntu Community will want to sign something to be able to read my file, I mean the linux community does not like to sign or agree to anything as far as I can tell.

I may end up asking if all else fails.

Thanks for the suggestion and the link 1fallen.:)

---

### Post by #&amp;thj^% on 2020-12-30
> **wildmanne39 said:**
> That does look a lot easier, I have esigned documents for my loans but that is it, I do not think users in the Ubuntu Community will want to sign something to be able to read my file, I mean the linux community does not like to sign or agree to anything as far as I can tell.

I may end up asking if all else fails.

Thanks for the suggestion and the link 1fallen.:)

I'll keep my thinking cap on in the meantime.
BTW just a thought are permissions ok with Evo

---

### Post by wildmanne39 on 2020-12-30
I solved the issue:

From the Evolution Main Menu, select Edit -> Preferences. In the left pane, select Mail Accounts. In the right pane, select the email account you are using -> Select the Security tab, then select the option Always trust keys in my keyring when encrypting and close, it was that simple.

Answer is from here:

[https://fedoraproject.org/wiki/Using_GPG_with_Evolution](https://fedoraproject.org/wiki/Using_GPG_with_Evolution)

Thanks 1fallen.

---

