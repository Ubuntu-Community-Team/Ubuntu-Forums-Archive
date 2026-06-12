---
title: "Problem with chrome or javascript or something like that?"
date: 2023-03-04
forum: General Help
---

### Post by gale85 on 2023-03-04
I'm currently learning to work in javascript and when I try to open it in chrome I get a message

crbug/1173575, non-JS module files deprecated.

Here is the code

```

let r = fetch('URL')
.then(response => response.json()).then(data => {
    console.log(data);
}).catch(error => {
    alert(error);
});

```
The url is correct and it works ok, but when I go to that network in chrome and offline, it doesn't give me the error I wrote in the code, but I get the above message.
I was looking for how to get rid of it when I get the message, but I don't know how to solve it, whether in Chrome or maybe Visual Studio or maybe some javascript update.

Ubuntu version 22.04

If you need more information, tell me

---

### Post by MAFoElffen on 2023-03-04
Go into the Network tab of the Chrome Developer Console. Be sure that the connection is set on to No throttling and not to Offline...

---

### Post by gale85 on 2023-03-04
I already set it to be offline to check if the script works and when the site won't load and then I get a message
crbug/1173575, non-JS module files deprecated.

A while ago I tried to change the URL and then everything works as it should, but why doesn't it happen when I put it offline in chrome, but it throws me a message in the top line[COLOR=#000000]

[/COLOR]

---

### Post by MAFoElffen on 2023-03-04
Where I looked, is said "NOT to offline..." That there was some kind of bug, that when set to offline, or to "no throttling" that it threw that error. It said it work on other settings. It did not describe the why of why it threw the error.

Sorry that I do not know more of the details on that.

---

### Post by gale85 on 2023-03-11
When I set it to offline in Network, it tells me that the site is not working, and in the console (chrome) I get the message "crbug/1173575, non-JS module files deprecated". When I change the url in the js code, it just won't execute the code and report the error exactly as I set it up. The only thing that bothers me is that when I set it to offline in Network, why does it throw out this message, but it doesn't show like that in the tutorial I'm following on YouTube. So I'm just trying to make sure it works normally even when I set offline. I hope it's clearer now

---

