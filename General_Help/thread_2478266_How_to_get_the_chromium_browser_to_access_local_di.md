---
title: "How to get the chromium browser to access local directories?"
date: 2022-08-21
forum: General Help
---

### Post by HippoMan on 2022-08-21
I'm running xubuntu (20.04), and I want to use the chromium browser.

However, it seems like Ubuntu's version of the chromium browser is "cripple-ware", *i.e.*, some standard browser functionality is missing ... in other words, chromium's browser functionality appears to be crippled.

I want to be able to access files within each and every one of my computer's local file systems via "file://" URL's and any other conventional manner. However, Ubuntu's chromium browser does not appear to be allowing me to access any of these local filesystems.

Is there any way I can run the chromium browser on my xubuntu system  such that it offers full access to all data on all local filesystems  along with all other normal browser functionality?

I hope that the answer is "yes"! ... but if not ...

I absolutely ***do not*** (!!!) want Ubuntu nor chromium itself to try protect me from myself. I have valid personal reasons for wanting to access data in local filesystems when using the chromium browser, and I know what's best for me. I take full personal responsibilty for the security of my system, and if the Ubuntu or chromium developers think they know better than I do about what's best for me, then this would be a serious case of misplaced arrogance on their parts.

Thank you very much in advance.

---

### Post by &amp;KyT$0P# on 2022-08-21
One way could be to install the [flatpak of Chromium]("https://flathub.org/apps/details/org.chromium.Chromium") instead of the snap, and if the default sandbox configuration of the Chromium flatpak doesn't let you browse the local files you want to browse, grant access using [Flatseal]("https://flathub.org/apps/details/com.github.tchx84.Flatseal").

If you don't have Flatpak set up, there are instructions on [its official website]("https://www.flatpak.org/").

---

### Post by HippoMan on 2022-08-21
Thank you very much! I'll try Flatseal.

But also, I just figured out a workaround using the standard snap package. All I have to do is to directly run the chromium browser as follows:

**/snap/chromium/current/usr/lib/chromium-browser/chrome**

Apparently, all of the browser-crippling capabilities are part of the snap-based chromium environment itself, but if I just run that executable directly from its location within the snap directory tree, those "features" get bypassed.

---

### Post by evinrude on 2022-08-21
So what happens when you  put a '~'  as a url ?

---

### Post by HippoMan on 2022-08-21
> **evinrude said:**
> So what happens when you  put a '~'  as a url ?

When directly running **/snap/chromium/current/usr/lib/chromium-browser/chrome** (not via snap itself), that URL just shows me an index of my home directory.

---

### Post by HippoMan on 2022-08-22
> **HippoMan said:**
> /snap/chromium/current/usr/lib/chromium-browser/chrome

Also, just in case a future *_apt_ *update of _*xubuntu*_ or the installed software tries to "fix" chromium so that running it directly via the above-mentioned path under _*/snap*_ no longer starts up a non-crippled browser, I copied the entire **/snap/chromium/current** directory to a second location on my computer, and I now run chromium via its path name at that second location. It still runs in a non-crippled manner.

---

### Post by evinrude on 2022-08-23
as a url '~/../..'

---

### Post by HippoMan on 2022-08-23
> as a url '~/../..' 			 		

Even though that might work with the standard chromium browser, what  does not work is accessing local files, for example, in order to do  uploads. When trying to upload content, the standard chromium browser  does not permit access to any directories outside of the HOME tree when  trying to go to thos directories via the upload file-selection dialog.

There might be workarounds for this, but it's much, much easier to simply run /**snap/chromium/current/usr/lib/chromium-browser/chrome**  directly, as I described above, and thereby get the same functionality  that is available in normal browsers ... with no workarounds necessary.  Users of other browsers are accustomed to being able to access local  files with their browsers, and this has been standard browser  functionality for decades. The users on my system should not have to  suffer with that functionality being crippled and therefore having to  make use of non-standard workarounds.

Something much more desirable for chromium would be some sort of new  command-line flag which tells the browser to start up in non-crippled  mode -- perhaps something like **--enable-local-access**. But I think  it's extremely unlikely that the powers-that-be at ubuntu would ever  approve such a fix for their crippled chromium browser.

---

