---
title: "borked Firefox with Firewall"
date: 2013-04-30
forum: General Help
---

### Post by SuperFreak on 2013-04-30
I installed the graphical interface for the Ubuntu firewall (gufw) and then disabled and unistalled it. Now Firefox is not always opening. It opens on startup because it is in the startup menu but after that it won't open. I thought there were no rules remaing after I diabled it but something is wrong.

tried ```
sudo ufw disable
```

help would be welcome as I can't use firefox easily anymore

---

### Post by Frogs Hair on 2013-04-30
UFW can be run from the terminal. but if you only installed the GUI enabled it and disabled it without making any rules I don't how that would affect Firefox. I use GUFW and after disabling and  removing I could not duplicate the error in Firefox. Some basic terminal commands for UFW  can be found at the link. 
[https://wiki.ubuntu.com/UncomplicatedFirewall](https://wiki.ubuntu.com/UncomplicatedFirewall)

---

### Post by steeldriver on 2013-04-30
Hmm... firewall rules shouldn't affect whether an application starts or not - what happens if you try to start firefox in a terminal? are there any error messages?

---

### Post by SuperFreak on 2013-04-30
I tried sudo firefox start after closing firefox and got a delay of about 2 minutes and then firefox opened normally with no errors.
Firefox no longer opens immediately

---

### Post by Frogs Hair on 2013-04-30
You don't need to open Firefox as root, but the terminal output should display errors that may indicate what's happening.
```
firefox 
```

---

### Post by steeldriver on 2013-04-30
I'd actually say DON'T run it with sudo - if your profile gets owned by root it will likely screw things up even more

---

### Post by SuperFreak on 2013-04-30
> **steeldriver said:**
> I'd actually say DON'T run it with sudo - if your profile gets owned by root it will likely screw things up even more
Noted,

The command ```
Firefox
``` did put out an error message as follows

```
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined

error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined

error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined
error: google-translate: An exception occurred.
Traceback (most recent call last):
  File "javascript:on("click", function (node) {  var url = node.href;postMessage({ url: url });});", line 1, in 
  File "resource://jid0-k75tfrgfoxphfezmj9cku5ecglc-at-jetpack/addon-sdk/lib/sdk/content/content-worker.js", line 256, in deprecatedOn
    console.error("DEPRECATED: The global `on()` function in content " +
ReferenceError: console is not defined


```

Would uninstalling Firefox , purging and then reinstalling it fix matters. I have my setings, bookmarks backed up on FEBE

---

### Post by SuperFreak on 2013-04-30
Not sure what happened but it is working fine now. It opened up after the Firefox command in terminal with all my addons on their web pages indicating they were just installed or upgraded and my home page changed to google search
Very strange

---

### Post by steeldriver on 2013-04-30
Do you have any addons related to translation (the errors seem to be related to something called google-translate)? if so it might be worth disabling those if it happens again

---

### Post by SuperFreak on 2013-04-30
Yes I have gogle translate. I will disable it

Thanks for your help

---

