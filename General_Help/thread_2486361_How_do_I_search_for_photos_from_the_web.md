---
title: "How do I search for photos from the web"
date: 2023-04-27
forum: General Help
---

### Post by jari169 on 2023-04-27
hi! How do I search for photos from the web camera on the website constantly on the server. but the browser doesn't update them.. how do I clear the browser with javascript... Or how do I update the images using javascript... Here you can see that the .gif images don't update with Chrome. What do I do when I open the browser like that the pictures are updated as soon as possible from the camera...

[https://raittiforum.liipparit.fi/](https://raittiforum.liipparit.fi/)
How repair?
.jari

<script>if (!location.hash) {
location.hash = "#just-update";
location.reload(true);
} else {
location.hash = "";
}
</script>

---

### Post by SeijiSensei on 2023-04-27
I'd add one of these extensions to Chrome to enable auto refresh. The page will update automatically on a fixed schedule.

[https://chrome.google.com/webstore/search/refresh](https://chrome.google.com/webstore/search/refresh)

---

### Post by jari169 on 2023-04-27
Thank you.. Maybe the extension doesn't work as it should in Chrome.. How can I fix the Script so that I can get it to work embedded in the home page also in the chrome browser, while the site works fine in the Firefox browser.
I think the browser cache should be reset somehow.

Firefox works fine when browsing, but Chrome doesn't feel like its own.
how fixset...
<script>if (!location.hash) {
location.hash = "#just-update";
location.reload(true);
} else {
location.hash = "";
}
</script>

---

### Post by SeijiSensei on 2023-04-27
There are three extensions in that list that provide auto-refresh. Did you try them all?

You can also add an HTTP header to automatically refresh the page. [https://www.stefanjudis.com/today-i-learned/how-to-refresh-a-page-in-an-interval-without-javascript/](https://www.stefanjudis.com/today-i-learned/how-to-refresh-a-page-in-an-interval-without-javascript/)

I've written a lot of websites. I rarely use Javascript. I prefer server-side processing via PHP.

---

### Post by jari169 on 2023-04-27
A better alternative is to find a complete homepage reload script (e.g.java-script..php.) with a manual button..  Can someone help

---

