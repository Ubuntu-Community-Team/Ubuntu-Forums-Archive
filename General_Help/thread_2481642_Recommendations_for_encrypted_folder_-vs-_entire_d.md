---
title: "Recommendations for encrypted folder -vs- entire drive, on 22.04 LTS"
date: 2022-12-05
forum: General Help
---

### Post by uacnt83982803 on 2022-12-05
What say the gurus on the topic of encrypting a folder to hold private data (using Veracrypt, for example) versus whole-disk encryption, on 22.04?  I just want to be sure my data is safe should my laptop be stolen.

I've used whole-disk encryption in the past but I am wondering if that's maybe not the best approach.

---

### Post by oldfred on 2022-12-05
I believe in only encrypting part of my data. Most is not really valuable. 
I created one partition with LVM & encryption.

We used Pareto at work a lot. That was the 80/20 to analyze data. Or 80% of sales, inventory, etc was from 20% of the SKU - stock keeping units.
While I have to use a key to get into my house I only have some data in a safe, not entire house. When I was a kid, we did not even lock house, but did have valuables locked in the bank or if computer data now, offsite backup.

---

### Post by ian-weisser on 2022-12-05
Data that is *sensitive* (damaging if disclosed) should be *encrypted*.
Data that is *valuable* (expensive or impossible to replace if lost) should be *backed up*.
Data that is both should be both.

Example: A treasured photo of your great-grandmother might be valuable (you treasure it), but it's probably not sensitive. It should be backed up to protect against loss, but there is little benefit to encrypting it.

Look at your data and know which is which...and which is neither.

- For sensitive personal data, a typical password-manager application (basically an encrypted database with a pretty frontend, integrated into your web browser) is often enough for most general-purpose users. Such a database is usually inconvenient to reconstruct, so should be backed up.

- If you need to encrypt more data, Ubuntu has tools to encrypt individual files or a whole directly conveniently. You don't need to manually decrypt them; they look to you like normal, editable files. Encrypted data that is valuable should be backed up.

- Whole-disk encryption is typically for enterprise- and government-grade systems to protect --along with other safeguards-- against the real threats of professional or state-sponsored espionage in your industry and attacks by organized crime. Usually the IT department that requires whole-disk encryption will also handle imaging your system for you and will have a backup policy for you to follow. If your organization doesn't have that kind of IT department, then maybe you might not need whole-disk encryption after all.

---

### Post by TheFu on 2022-12-05
If the entire OS isn't encrypted, then hacking that and gaining access to the data can be handled later, via automation, once the encrypted data is unlocked and mounted.

Just sayin'.

For portable devices, encrypt everything.  A travel buddy/business partner had 2 devices stolen on a trip in 2 days.  We didn't know when the first theft happened.  Just sometime in these 4 hrs.  the next day, we were at a nice restaurant having an epic meal at the "chefs" table when 2 20-something locals came into the building, into the back room and started making lots of noise and movements, then they left and 2 smartphones were gone.  We spent the rest of the day shutting down access to systems and at the local police station.  That night, the friend spent on the phone getting all his credit cards and bank accounts changed.  He'd been traveling the world for years and had been to about 80 countries, so he wasn't some noob traveler.  For the next 6 months, everyone in his contacts was receiving phishing attempts seeking money using every method - from "he's in a foreign jail and needs $2000K to bribe the guards" to "pay this bill $485.29 for software XYZ" that the company actually used.  We also got phone calls using some information he had in the contacts, like wives' birthdays.  About 4 months after the phones were stolen, we were able to trace them.  One was in central Africa and the other was in Indonesia.  The phones were stolen while we were in Europe. Many countries have a shared "stolen device" data base that the telcos use to refuse service for stolen devices, so they couldn't sell those high-end phones to be used in Europe or N. America or Japan/SK. 

Encrypt everything and use a 2FA device to gain access.
If you want to encrypt more inside the whole storage encryption, fine. Do that too.

Look up the "evil maid attack" for why you don't want to let any devices out of your sight and why when traveling you probably want to boot from USB or flash storage, not the internal storage.  When I'm in poorer countries, I definitely have a separate boot flash device on my person when it isn't actively used to boot a computer. It goes into the shower with me on a microSD card and the computer in the other room is completely shutdown, if I'm not using it.

---

### Post by HermanAB on 2022-12-06
More travel tips: Mix up your ID while traveling.  Use a credit card from one country and a driver’s license or passport from another country. Never give your passport to a hotel - use an ID card instead, since a passport is a complete ID theft kit including your address and signature. Also don’t sign your credit cards.

---

### Post by dragonfly41 on 2022-12-06
I use Tresorit.com. But don't mislay the master password.

---

