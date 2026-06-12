---
title: "How did I configure my browser to not download large images?"
date: 2017-05-24
forum: General Help
---

### Post by muscogulus2 on 2017-05-24
Chromium does not download images above a given threshold; I think it is 500 KB. I did this deliberately and would like to undo it. 

Only trouble is, I can't remember what I did, cannot find the setting, and have done four web searches without helpful results. 

What did I do?

---

### Post by &amp;KyT$0P# on 2017-05-24
What Chromium extensions do you have?

---

### Post by vasa1 on 2017-05-24
> **halogen2 said:**
> What Chromium extensions do you have?

+1. That would be interesting to know. 

@OP, So what do you see with a large image? Is a place-holder left behind with a link you can click on if you do decide to view the large image?

---

### Post by vasa1 on 2017-05-24
I don't use many extensions or visit the extensions site much and so I don't know of an extension for Chrome/Chromium to list one's extensions.

As a workaround, I opened *chrome://extensions/* and saved the page in *~/Downloads*. There, in a folder called */home/vasa1/Downloads/Extensions_files/*, there is *saved_resource(1).html*.

I grepped that file like this:
```
grep "extension-title" "saved_resource(1).html"
.extension-title {
.inactive-extension .extension-title {
          <span class="extension-title command-title">Stylish - Custom themes for any website</span>
          <span class="extension-title command-title">uBlock Origin</span>
          <span class="extension-title command-title">uBlock Origin Extra</span>
          <span class="extension-title command-title"></span>
          <h2 class="extension-title">Google Docs</h2>
          <h2 class="extension-title">Google Docs Offline</h2>
          <h2 class="extension-title">Google Sheets</h2>
          <h2 class="extension-title">Google Slides</h2>
          <h2 class="extension-title">Stylish - Custom themes for any website</h2>
          <h2 class="extension-title">uBlock Origin</h2>
          <h2 class="extension-title">uBlock Origin Extra</h2>
...
          <h2 class="extension-title">uMatrix</h2>
          <h2 class="extension-title"></h2>
    <span class="dep-extension-title"></span>

```

---

### Post by again? on 2017-05-25
uBlock Origin has such a setting.
Other blocker extensions may have similar.

---

### Post by muscogulus2 on 2017-05-25
> **halogen2 said:**
> What Chromium extensions do you have?

Aha! It's a setting in uBlock Origin. "Block media elements larger than [NN] KB." 

Thanks. Somehow I convinced myself it was not a browser extension.

---

### Post by muscogulus2 on 2017-05-25
> **vasa1 said:**
> +1. That would be interesting to know. 

@OP, So what do you see with a large image? Is a place-holder left behind with a link you can click on if you do decide to view the large image?

Yes. If the placeholder isn't sized properly in the page markup, it won't appear the correct size on the page. (You can tell who specified WIDTH but nor HEIGHT, for example.) 

Clicking the link is supposed to download the file, usually an image. 

Some sites (Facebook, Medium) effectively prevent that by making all image placeholders interactive. So instead of the empty placeholder, you see an overlay with an empty placeholder.

---

