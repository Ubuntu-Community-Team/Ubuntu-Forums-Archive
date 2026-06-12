---
title: "Ubuntu 18.04 LTS Python3 version"
date: 2019-06-12
forum: General Help
---

### Post by maximrub on 2019-06-12
Hello,
I wanted to ask if the default Python3 version on Ubuntu 18.04 LTS will always be on the Python 3.6.x branch or it might update to 3.7 in the future?
If it will b updated to 3.7 is there a time frame for this?
Thank you,
Maxim

---

### Post by oldfred on 2019-06-12
Whatever you do, do not ever change default versions of python in Ubuntu.
You can add additional versions, if you really want but rarely required.

Ubuntu used to never update any applications, but would back port major security issue fixes.
 Now it does update Firefox & Thunderbird, as I guess it is easier to update entire application than re-verify that older version with back ported fixes works.

But a lower level application like python would require it to work with every application that uses python, so I would not expect it to every change. If a major security issue is found, they normally would only back port or add just that fix.

You can relatively easily add another 25GB partition and dual boot. Then you can also have the newest Ubuntu with latest python3 for testing if desired.
If newer hardware, you also can install Ubuntu in a VM so both are running at same time to make it easy to switch.

---

### Post by maximrub on 2019-06-15
I don't want to install 3.7. I want to make sure the default python 3 version will be 3.6.x, as in the past it was 3.6.5 and now it's 3.6.7.

---

### Post by ajgreeny on 2019-06-15
Why is this so important to you?

I have no idea how secure that it would be if you did so, and I would most certainly recommend you do not do so, but you can pin the current version of any package if it is essential to you.

As python3 has hundreds of separate packages, most of which will not be installed on your default system, I am not sure how easy it will be to ensure that none of those that are installed (I have about 82 python3 packages in my system) ever upgrade to version 3.7.

---

### Post by kpatz on 2019-06-15
Typically once package versions are determined for a release (LTS or not) they are frozen and only bugfixes and security updates are applied during the life of the release.

My Python3 version in my 18.04 install is 3.6.8.  I expect future updates will just update the 3rd "dot" (3.6.9, 3.6.10 etc.) but it will stay on 3.6.x for the life of the LTS release.

If a newer version of Python is stable when the next Ubuntu release is frozen, it will likely be included in that release.  16.04 has Python3 version 3.5.2 and 19.04 has 3.7.3 currently.

---

### Post by monkeybrain20122 on 2019-06-15
It will stay in 3.6.x, currently it is 3.6.8, when Ubuntu 18.04 was first released it was 3.6.4 or something like that.

---

### Post by TheFu on 2019-06-15
If you are a python developer and need complete control over the specific version of python and associated modules, then using a python environment tool is the best practice.  Something like **pyenv**.  If you are making a trivial tool for use on the OS, great, use the OS packaged versions.  If you are making a complex webapp that is the sole purpose for the server existing, then you should control the entire python environment that your webapp needs to run well.

The python version and all the modules installed via APT are maintained by Canonical for their needs and we get to live with the fallout for any changes they make.

These are the best practices for all scripting languages and why rbenv, perlbrew, pyenv, and all the other similar tools for all the other scripting languages exist.

---

