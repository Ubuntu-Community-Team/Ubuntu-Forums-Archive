---
title: "Thunderbird - Unable to send mail and lost addresses"
date: 2021-04-26
forum: General Help
---

### Post by arst06d on 2021-04-26
Hi

I have a dual boot system Xubuntu and Win10.  I only installed Win10 as I needed to use ZOOM for playing music - the linux client does not offer the same features as the Win client (as usual).  Had been getting along nicely, dual booting .  Win10 has just required an update - and it destroyed the booting - couldn't access Xubuntu from GRUB - gave me a Kernel Panic after saying "Invalid ELF Header".
Tried to use the LiveCD, downloaded Boot-repair but it wouldn't run as it said needed access to a repository.
I downloaded and burned Boot-Repair-Disk and booted from that - no change when I tried to boot from the Grub.

While in LiveCD I attached a USN HDD and copied my home directory to it, bit the bullet and reinstalled Xubuntu 20.04 LTS plus updates etc.

I could boot into the new installation - hurrah.  However, something screwy with permissions on my home folder - all as root.  So I used sudo chown -R david:david /home/david/ to claim ownership and all seemed well.

Opened Thunderbird for the first time and all my accounts and existing emails (POP) were there.  I can download new emails for all accounts, no errors.

However, My address book had disappeared - nothing in it even though the abook.mab was copied across.

I can also not send emails from any account.  It gives no error, just does nothing when I click the Send button.

When I type in a valid email address in the To field and press enter - nothing happens.  Doesn't recognise it (obviously no lookup to an address book) but just stays red and have to manually click in the next field - won't tab away from the To field.

Weird and frustrating.

I have just copied the .thunderbird folder to a USB again, deleted the old folder.  Using Synaptic Package Manager I completely removed Thunderbird, then reinstalled.  Again did CHOWN on my home folder.  Still no address book in Thunderbird and cannot send emails.

Also tried replying to a received email.  The address is something like First Last <firstlast@gmail.com>      This appears in red and the Send button is greyed out.  I have to remove everything but the contents between < and > to get the Send button to be enabled - but then nothing happens when I press it.

As I say receiving mail is no problem.  I have checked the SMTP server settings and all seems fine - same settings as on my phone which works no problem.

Urgent assistance please!

---

### Post by arst06d on 2021-04-28
OK some progress with this.

It appears that the lost address book and the inability to send mail is linked.

I gather that Thunderbird no longer uses the .mab files for the address book - rather it now uses .sqlite files (abook.slite, history.sqlite).  The presence of the .mab files is a hangover from upgrades of TB not tidying up after itself.

I closed TB, created a SAVED folder in .thunderbird and moved all .mab and equivalent .sqlite files there.  Reopened TB and it had created new .sqlite file - but no .mab files.  I can now send mail again, and the empty address book is getting populated from the mail I just sent.

So, at the moment I have lost my address book.  I tried moving the new .sqlite files and replacing with the old .slite files but again no address book so reverted to the option of being able to send mail again.

The question now becomes:  How do I recover dater from the old TB .sqlite address book files and repopulate the new .sqlite files?

---

### Post by TheFu on 2021-04-28
Interesting.
```
$ file abook.mab.bak
abook.mab.bak: Mozilla Mork database, version 1.4
```
That's a new mime type to me. I'm happy to be using an LDAP addressbook. ;) 

```
$ file abook.sqlite abook.sqlite-wal
abook.sqlite:     SQLite 3.x database, user version 2, last written using SQLite version 3031001
abook.sqlite-wal: SQLite Write-Ahead Log, version 3007000

```

Maybe there is a way to convert a mab --> sqlite?
[https://support.mozilla.org/en-US/questions/1306681](https://support.mozilla.org/en-US/questions/1306681) claims that if there aren't any sqlite files with abook in the name, but there is a abook.mab, then when thunderbird starts, it will automatically perform the conversion.

---

### Post by arst06d on 2021-04-28
[www.recoverytools.com/blog/thunderbird-new-address-book/](www.recoverytools.com/blog/thunderbird-new-address-book/) gives some info - it appears that I was was right in that the .mab files are redundant and have been replaced by .sqlite equivalents.  Their presence is a by-product of upgrades of TB not clearing up after itself.

I had moved all the .mab and .slite files to a SAVE folder, and TB created new .sqlite file but not .mab files.  As a test, I moved the new .sqlite files (containing just your email address) to a second SAVE folder and copied the originals back.  Restarted TB and the old problem was back.  Reversed the process - no problems.

So - obviously I don't have to extract the data from the .mab files because it will not be current (although I still have that option to recover at least much of the abook), but there seems to be an incompatibility or corruption in the .sqlite file.  I downloaded a sqlite DB utility and it can open the files OK so doesn't look like a corruption, so down to incompatibility of some sort. 

I don't know if TB stamps the .sqlite data in some way but there you go.

Now my DB Browser for SQLite gives me the option to export and import so, girding my loins I exported the Cards and Properties from the saved abook.slqite to a text file and imported into the current TB .slite file - it worked!  So I did the same with history.sqlite - that worked too!

It appears I now have a fully functioning TB with populated address book - yahoo!

The question remains - why is nothing ever easy?

---

### Post by ActionParsnip on 2021-04-28
Did you set the owner to the user on the new system after you restored it?

---

### Post by arst06d on 2021-04-28
> **ActionParsnip said:**
> Did you set the owner to the user on the new system after you restored it?

If you read my initial post you see that I did.

However, this is now solved as detailed above.

---

### Post by TheFu on 2021-04-28
> **arst06d said:**
> The question remains - why is nothing ever easy?

It was easy for me. Didn't have to do anything manually.  The mab --> sqlite conversion was automatic. I didn't do **anything**.

---

