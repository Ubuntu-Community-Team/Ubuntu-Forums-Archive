---
title: "any faster ways to generate a list of urls from a website into a text file?"
date: 2018-12-01
forum: General Help
---

### Post by ardouronerous on 2018-12-01
This is the wget code I used:

```
wget -c --retry-connrefused --tries=0 --timeout=5  --spider -r https://en.uesp.net/wiki/Morrowind:Morrowind 2>&1 | grep '^--' | awk '{ print $3 }' | grep -v '\.\(css\|js\|png\|gif\|jpg\|JPG\)$' > urls.txt
```

After 6 hours of waiting for this to finish, I finally gave up, I canceled the process. 6 hours is way too much.

Is there a faster way?

---

### Post by freemedia2018 on 2018-12-01
I was going to recommend a tool that was in Ubuntu years ago, but since it isn't in the repos anymore I wont do that. I only just found out it's not included anymore.

You could try changing --tries=0 to 5. --tries=0 probably means "keep trying no matter what." Be sure that your connection is fast enough to download an entire wiki in 6 hours. Each of those pages has more HTML than people usually think about, it adds up.

---

### Post by ardouronerous on 2018-12-01
> **freemedia2018 said:**
> Be sure that your connection is fast enough to download an entire wiki in 6 hours. Each of those pages has more HTML than people usually think about, it adds up.

My connection is 2mps, we want to upgrade to 5mps, but our ISP says that speed isn't available in our area.

> You could try changing --tries=0 to 5. --tries=0 probably means "keep trying no matter what."

My reason for making --tries=0 is because our internet connection is affected by rain, so we lose connection whenever it rains.

---

### Post by SeijiSensei on 2018-12-02
If you just want a list of the URLs on a page, and not their content, there are Firefox add-ons for this task like this: [https://addons.mozilla.org/en-US/firefox/addon/urls-list/](https://addons.mozilla.org/en-US/firefox/addon/urls-list/)

---

