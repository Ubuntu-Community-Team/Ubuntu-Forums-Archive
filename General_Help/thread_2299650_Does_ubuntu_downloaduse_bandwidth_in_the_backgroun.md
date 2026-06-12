---
title: "Does ubuntu download/use bandwidth in the background?"
date: 2015-10-20
forum: General Help
---

### Post by Ridwan_Sameer on 2015-10-20
Hello,

I'm pretty new and just installed ubuntu and got it working with my dual boot after a long and tiresome process.

I live on a 50GB per month connection, so I don't want things updating/installing automatically. Does this happen with ubuntu? For example I installed the nightly build for the Cinnamon Desktop environment, does it automatically update to the latest build without my knowing?

And are there any other cases where things automatically update etc?

Thank you

---

### Post by howefield on 2015-10-20
You have control over the updates, including setting the frequency of update checking and whether or not available updates are automatically installed.

---

### Post by Ridwan_Sameer on 2015-10-20
> **howefield said:**
> You have control over the updates, including setting the frequency of update checking and whether or not available updates are automatically installed.

Thank you, it was set to check for updates daily, but only set to display updates and not download them.

Is ther anything else that is not specific to ubuntu? Maybe linux automatically downloads the latest of something? For example, when I use sudo apt-get updates, it only lists the new versions not actually downloads them, yes?

---

### Post by slickymaster on 2015-10-20
> **Ridwan_Sameer said:**
> Thank you, it was set to check for updates daily, but only set to display updates and not download them.

Is ther anything else that is not specific to ubuntu? Maybe linux automatically downloads the latest of something? For example, when I use sudo apt-get updates, it only lists the new versions not actually downloads them, yes?

Yes, **apt-get update** only resynchronizes the package index files from their sources; **apt-get upgrade** is the command used to install the newest versions of all packages currently installed on the system from the sources enumerated in **/etc/apt/sources.list**

---

### Post by howefield on 2015-10-20
> **Ridwan_Sameer said:**
> Is ther anything else that is not specific to ubuntu?

Uhm.. there may be third party software that checks for available updates but I'm not sure of any that would automatically download the update, an example might be Virtualbox which will check for an updated version and ask you if you want to download it. Any applications that do that should have a setting in preferences for toggling the check.

> Maybe linux automatically downloads the latest of something? For example, when I use sudo apt-get updates, it only lists the new versions not actually downloads them, yes?

That's correct apt-get updates only updates your list of package version numbers to match the repository versions but doesn't download packages to which there is an update. You will see notification of the size of the download after typing the apt-get upgrade command but before you confirm.

---

### Post by Ridwan_Sameer on 2015-10-20
Thanks for the replies.

lastly, is there any bandiwdth monitoring tool for ubuntu? Back on Windows I used Glasswire, I don't think there is a Linux version

---

### Post by vasa1 on 2015-10-20
One possible exception is Dropbox. That one updates automatically on my system. My Dropbox is direct from dropbox.com; not from the repos.

Then, you need to make sure you don't sync your browsers or anything else to the cloud or to Dropbox.

Why don't you take an "unlimited" plan, maybe one of lower speed?

---

### Post by slickymaster on 2015-10-20
> **Ridwan_Sameer said:**
> Thanks for the replies.

lastly, is there any bandiwdth monitoring tool for ubuntu? Back on Windows I used Glasswire, I don't think there is a Linux version

You could try [BitMeter OS]("https://codebox.org.uk/pages/bitmeteros")

---

### Post by Ridwan_Sameer on 2015-10-20
> **slickymaster said:**
> You could try [BitMeter OS]("https://codebox.org.uk/pages/bitmeteros")

Running the BitMeter OS Web interface gives me a server not found error :(

---

### Post by howefield on 2015-10-20
> **Ridwan_Sameer said:**
> Thanks for the replies.

lastly, is there any bandiwdth monitoring tool for ubuntu? Back on Windows I used Glasswire, I don't think there is a Linux version

Long time since I used a network bandwidth monitor, but when I did, I used vnstat. It's a command line tool but very easy to use.

Quite simple and low resources. It is in the repository so very easy to get up and running.

---

### Post by slickymaster on 2015-10-20
> **Ridwan_Sameer said:**
> Running the BitMeter OS Web interface gives me a server not found error :(

In a terminal window the following commands will stop/start/restart the OS BitMeter Web Interface```
sudo /etc/init.d/bitmeterweb stop
sudo /etc/init.d/bitmeterweb start
sudo /etc/init.d/bitmeterweb restart
```

---

