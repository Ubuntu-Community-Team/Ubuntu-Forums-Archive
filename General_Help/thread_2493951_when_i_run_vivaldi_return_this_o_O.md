---
title: "when i run vivaldi return this o_O"
date: 2023-12-31
forum: General Help
---

### Post by faustf2 on 2023-12-31
hi guys  good year  ,  why  when i run vivaldi browser  return me this error ? 
```
[3910:3910:1231/154947.149137:ERROR:vaapi_wrapper.cc(1105)] Empty codec maximum resolution
[3910:3910:1231/154947.149265:ERROR:vaapi_wrapper.cc(1014)] FillProfileInfo_Locked failed for va_profile VAProfileH264ConstrainedBaseline and entrypoint VAEntrypointVLD
[3910:3910:1231/154947.149368:ERROR:vaapi_wrapper.cc(1105)] Empty codec maximum resolution
[3910:3910:1231/154947.149451:ERROR:vaapi_wrapper.cc(1014)] FillProfileInfo_Locked failed for va_profile VAProfileH264Main and entrypoint VAEntrypointVLD
[3910:3910:1231/154947.149527:ERROR:vaapi_wrapper.cc(1105)] Empty codec maximum resolution
[3910:3910:1231/154947.149603:ERROR:vaapi_wrapper.cc(1014)] FillProfileInfo_Locked failed for va_profile VAProfileH264High and entrypoint VAEntrypointVLD
[3910:3910:1231/154947.155636:ERROR:sandbox_linux.cc(374)] InitializeSandbox() called with multiple threads in process gpu-process.
[3876:3876:1231/154947.236078:ERROR:vivaldi_ui_web_contents_delegate.cc(42)] UI Process abnormally terminates with status 3 after running for 0.171082 seconds!
[3876:3876:1231/154947.240435:ERROR:vivaldi_ui_web_contents_delegate.cc(73)] Quiting Vivaldi

```
i suppose  i VGA ???   i have  this vga ```
lspci | grep VGA
03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cape Verde XT [Radeon HD 7770/8760 / R7 250X]

```

---

### Post by MAFoElffen on 2023-12-31
The Vivaldi Forum, links this article as resolving this type of issue: 
[https://www.ghacks.net/2023/07/12/chromium-based-browsers-are-not-loading-pages-properly-on-linux-heres-how-to-fix-it/](https://www.ghacks.net/2023/07/12/chromium-based-browsers-are-not-loading-pages-properly-on-linux-heres-how-to-fix-it/)

---

### Post by faustf2 on 2023-12-31
> **MAFoElffen said:**
> The Vivaldi Forum, links this article as resolving this type of issue: 
[https://www.ghacks.net/2023/07/12/chromium-based-browsers-are-not-loading-pages-properly-on-linux-heres-how-to-fix-it/](https://www.ghacks.net/2023/07/12/chromium-based-browsers-are-not-loading-pages-properly-on-linux-heres-how-to-fix-it/)

thanks  so much but the  link is  if  you have white vivaldi , page ,  at me not start , and other chromium browser work perfect

---

