---
title: "Unable to customize Firefox 1.0.2"
date: 2005-04-17
forum: General Help
---

### Post by Annie Versary on 2005-04-17
Hi there,

though in other respects I'm very pleased with Hoary Hedgehog (Kubuntu 5.04) - as I've been with previous releases  :razz: - I'm now facing the following problem (apparently due to a special Ubuntu-flavour of the firefox 1.0.2 I've installed via apt).

Unlike in other distros I'm currently using or the ones I have used earlier (like warty warthog) there seems to be absolutely no way to install themes or extensions to this special (K)Ubuntu version (Help menu shows "Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.7.6) Gecko/20050405 Firefox/1.0 (**Ubuntu** package 1.0.2)").

First of all a click on the progress-indicator (top right) doesn't lead to the Firefox homepage but tries to open a "usr/share/ubuntu-artwork/home/index.html" that "cannot be found". Trials to install firefox-extensions via Tools/Extensions/Get More Extensions at best caus error messages like "Firefox could not download the file at [https://addons.update.mozilla.org/extensions/undefined](https://addons.update.mozilla.org/extensions/undefined) because: Not a valid install package" (though OS and version correctly chosen). 

The **JavaScript console output** either looks like 

[I]"XML Parsing Error: no element found
Location: jar:resource:///chrome/toolkit.jar!/content/mozapps/update/updates.xml
Line Number 1, Column 1:"[/I]

or like

*Error: uncaught exception: [Exception... "Component returned failure code: 0x80520012 (NS_ERROR_FILE_NOT_FOUND) [nsIWebNavigation.loadURI]"  nsresult: "0x80520012 (NS_ERROR_FILE_NOT_FOUND)"  location: "JS frame :: chrome://global/content/bindings/browser.xml :: loadURIWithFlags :: line 166"  data: no]*

Any idea how to fix this?

Thanks in advance...

Annie

---

### Post by benplaut on 2005-04-17
did you install Java Runtime Environment>

it appears to have something to do with it  :???:

---

### Post by dataw0lf on 2005-04-17
I moved this thread (the forum it was previously in is not for questions).  And it doesn't have anything to do with the JRE, although I'm unsure exactly what the problem is.  Researching now.

---

### Post by Annie Versary on 2005-04-17
@ benplaut:

Don't think that the reason can be the (non-) installation of a jre cause in the other distros I mentioned (and even under windoze) I had the Java Option unchecked and had no problems at all. 

And - just for the sake of completeness: I have Java installed 

java -version 'notes':

SableVM version 1.1.8
- compile date and time: 2005-01-01 19:42:12 UTC
- gcc version: 3.3.5 (Debian 1:3.3.5-5)
- 'real life brokenness' features enabled
- copying garbage collection
- bidirectional object layout
- direct-threaded interpreter


IMHO it must be a "JavaScript-thing" cause even a not-clicking-any-JS-link-session produces JavaScript-Console output like this:

[I]"XML Parsing Error: no element found
Location: jar:resource:///chrome/toolkit.jar!/content/mozapps/update/updates.xml
Line Number 1, Column 1:"[/I]

Besides: I'm quite sure to remember an online article saying that this functionality depends on where Firefox (or at least the chrome-folder?) is located/installed - plausible?

Annie

---

### Post by wmcbrine on 2005-04-17
I haven't experienced this problem, but I'd like to suggest [www.extensionsmirror.nl](www.extensionsmirror.nl) in place of the default "Get More Extensions" URL. It has a wider selection, is more up-to-date, and who knows? It may also solve your problem. I installed all my extensions from there, but that was before I upgraded to 1.0.2 (or 1.0.1 for that matter).

---

