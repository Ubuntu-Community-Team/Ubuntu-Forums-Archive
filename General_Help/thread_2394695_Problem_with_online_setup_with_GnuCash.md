---
title: "Problem with online setup with GnuCash"
date: 2018-06-20
forum: General Help
---

### Post by waltd on 2018-06-20
I am new to GnuCash. My OS is Ubuntu Unity 16.01 LTS. I created a new GnuCash file with new accounts. I tried to run the Online setup for my checking account. During the setup, I reach a point when I'm asked to run the AqBanking Wizard. When I click on the AqBanking wizard nothing happens and the GnuCash application closes or crashes. When I restart GnuCash I get this strange message:  GnuCash could not obtain the lock for file:///home/walter/GnuCash/Book01.gnucash.  (Book01 is the new GnuCash file). Any ideas on how to solve this problem so that I can create an online connection with my accounts?

---

### Post by Bob_Younkin on 2018-06-22
I have been using Gnucash for years. This has happened to me periodically if the computer closes without closing Gnucash first.
Databases lock the file to prevent a second person opening it.  When Gnucash crashes, it doesn't remove the lock.  The next time you login you get the error message you noted. I get an option to "open anyway".  I have not has a problem opening the file although Gnucash will sometimes rename the file "conflicted copy".
I have never been able to make AqBanking work on American banks.  I think it is intended for European banks.  I have had to be content to download *.ofx files of my accounts and load them the import faciliity.  Be sure that you have the correct account ledger open when you hit download.

Bob

---

