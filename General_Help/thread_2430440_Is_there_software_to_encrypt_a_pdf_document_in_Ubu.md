---
title: "Is there software to encrypt a pdf document in Ubuntu 16.04?"
date: 2019-11-01
forum: General Help
---

### Post by AbleTassie on 2019-11-01
I am using Ubuntu 16.04 LTS. I would like to encrypt a pdf document so that it can be sent attached to an email and opened by the recipient with a password that I send via a secure method. Is there software to encrypt a pdf document in Ubuntu 16.04? I would prefer something free and in the repos if possible.

Thank you,


A.

---

### Post by uRock on 2019-11-01
VeraCrypt can be used to make a small encrypted container, but it would require the recipient to use the same software. If you do this regularly, then using encrypted email would be a better method. [https://support.mozilla.org/en-US/kb/digitally-signing-and-encrypting-messages](https://support.mozilla.org/en-US/kb/digitally-signing-and-encrypting-messages)

---

### Post by Holger_Gehrke on 2019-11-01
If you're talking about turning an unencrypted pdf file into an encrypted one with a user and / or owner password with various restrictions set for users, than the command line tool qpdf from the repositories can do that. If you are generating the pdf yourself and the source material from which you're generating it is some kind of LibreOffice / OpenOffice document, then you can simply set the password(s) and the applicable restrictions in the export dialog.

Holger

---

### Post by Dennis N on 2019-11-01
> **AbleTassie said:**
> I am using Ubuntu 16.04 LTS. I would like to encrypt a pdf document so that it can be sent attached to an email and opened by the recipient with a password that I send via a secure method. Is there software to encrypt a pdf document in Ubuntu 16.04? I would prefer something free and in the repos if possible.

I would use gpg encryption. For that, you need the gnupg package. You can use a passphrase to both encrypt and decrypt, or a public/private key pair. **gnupg** uses terminal commands to encrypt and decrypt the document, or if you want a GUI to handle this, install **seahorse** and **seahorse-nautilus** in any supported Ubuntu version.

---

### Post by TheFu on 2019-11-01
+1 for using gpg.  But the setup is non-trivial and non-portable.  The entire message is encrypted this way.  Thunderbird + enigmail addon.  Probably need to have pinentry installed too, so the gpg keys can be unlocked.

For non-technical people, the only way I've been able to get them to understand was with a **ZIP** file that has a password on it.  That's how I deal with my accountant.  It was a major thing to get them to actually encrypt ZIP files and send them to me.  ZIP being cross-platform helps too.  I set an acceptable, long, passphrase that we'd use. There are ZIP cracking tools which can brute-force billions of passwords/second.  
ZIP isn't perfect. There are many more secure choices, but it is something normal people can understand and use.  Just be certain to use a long, somewhat random, passphrase with ZIP passwords.

None of these are PDF-specific.  They work with any files.

---

### Post by Skaperen on 2019-11-01
IOW, a PDF is just stored, attached to email, and encrypted, like any other kind of file.  that's because it is a file.  you don't need to compress a PDF file, though, because it already uses compression.  but, if you do compress it, it will not be ruined.  just uncompress it to get it back.  ZIP compresses it.  but that's no big deal.  it will be uncompressed when it is unzipped.  each of your documents is stored in an individual file.  be sure you save backups of them all somewhere that you know where they are.  do this frequently as they are edited.

---

### Post by HermanAB on 2019-11-02
I agree with TheFu that ZIP is the only encryption method that ordinary mortals can understand.  So you have to pick the method according to your audience.

---

### Post by uRock on 2019-11-02
> **HermanAB said:**
> I agree with TheFu that ZIP is the only encryption method that ordinary mortals can understand.  So you have to pick the method according to your audience.

Another +1 for this. Methods like the one I mentioned are tedious for non-techies.

---

### Post by The Cog on 2019-11-02
You can use gpg with a symmetric cipher. I thnk that is what AbleTassie is asking for. 
**gpg -c filename** will ask you for a passphrase and create filename.gpg. send filename.gpg and (by other means) the passphrase to your recipient. Recipient uses **gpg -d filename.gpg** and gets asked for the decryption passphrase.

However, I gather that PDFs have their own encryption - just as Holger_Gehrke says - if you are generating the PDF yourself use the encryption option in the creating software. PDF readers recognise such PDFs as encrypted and ask for a passphrse when you try to open them - no extra software needed.

---

### Post by TheFu on 2019-11-02
Not all PDF readers can handle PDF passwords.  

Additionally, any PDF file using the PDF standard newer than v1.6 will be tougher for F/LOSS people.  

If you want to make it hard for Ubuntu users, use Adobe PDF tools or use the newer than v1.6 PDF standard files.  Pretty much all F/LOSS PDF tools can handle 1.6 and older PDF files.  Just for clarity, this isn't about the version of Acrobat .... the PDF file specification has versioning. That's what's important.

---

### Post by kurt18947 on 2019-11-02
> For non-technical people, the only way I've been able to get them to understand was with a **ZIP**  file that has a password on it.  That's how I deal with my accountant.   It was a major thing to get them to actually encrypt ZIP files and send  them to me.  ZIP being cross-platform helps too.  I set an acceptable,  long, passphrase that we'd use.

I've read 7zip encrypted files are a little harder to crack than zip. Be sure to encrypt the file name as well as the contents. I don't know how true this is, I also don't know if most users can easily decrypt .7z files.

---

### Post by AbleTassie on 2019-11-11
Thanks to everybody for their replies. I eventually went with zip encryption with a long, somewhat random password as recommended.

A.

---

