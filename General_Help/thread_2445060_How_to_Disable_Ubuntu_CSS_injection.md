---
title: "How to Disable Ubuntu CSS injection"
date: 2020-06-08
forum: General Help
---

### Post by speatzle-2 on 2020-06-08
Hi,
I have noticed for a while that certain Linux Distros change how websites look presumably with CSS injection. How can i disable this? It's really Annoying and just strait up breaks certain sites and more importantly web apps that i have to use for work.

---

### Post by roboticforest on 2020-06-09
I've never heard of any OS doing this, but if Ubuntu is I'd be curious to know. Which flavors of Ubuntu are you referring to?

Have you checked the settings in your web browser? Particularly the appearance section and the accessibility section. Everything in those two areas should be able to override the CSS on any website that is loaded.

---

### Post by QIII on 2020-06-09
Are you sure it's *Ubuntu* -- or is it a malicious, possibly successful, attack launched from a website?

---

### Post by speatzle-2 on 2020-06-10
This is happening on a Fresh Standart Ubuntu 20.04 install with Firefox. This also happens on PopOS (there i have noticed that checkboxes are yellow in eg. roundcubemail).

Here are some screenshots of the differences between Windows and Ubuntu from a project i am working on for work:

[https://imgur.com/a/3CFonvH](https://imgur.com/a/3CFonvH)

The only explanation i can think of is that somehow css is either injected / changed or interpreted differently as those are all just simple text input html tags with css styling

---

### Post by QIII on 2020-06-10
That looks like one of two things to me, the latter being the most likely:

1.  Minor differences in Firefox built for Linux versus Windows.

2.  Your desktop theme.

---

### Post by speatzle-2 on 2020-06-12
How could a desktop theme influence websites? I haven't configured any themes so the default desktop them changes how websites look and even break layouts?

---

### Post by lvm on 2020-06-12
Make sure that you are using the same versions of firefox and firefox extensions, ensure that all settings are the same by copying firefox profile and that both systems have the same fonts installed.

---

### Post by sdsurfer on 2020-06-12
There are a couple things.

Form controls such as input buttons and select lists come from the ***system.*** This has been one of the greatest challenges for web developers since the beginning, they are very difficult to style and most of the time have to use workarounds - for example, a Javascript driven scheme that hides the actual form control and builds a "mock" out of elements that can be styled. This is definitely what you are seeing in the input buttons. It's not that the system is injecting anything, it's that the browser is saying "hey system, give me a submit button" and that is what it produces. This approach has its own problems in terms of SEO, WAI/accessibility compatibility, and screen readers. For example, many developers use an anchor element (link) and style it like a button, then apply Javascript form.submit(). Now the form no longer has an actual submit button and is JavaScript-dependent.

I'm not sure what's going on with the bars at the top or text input fields, those **should** be able to be styled without browser or system dependence. In any case, it's hard to say, the developer (is that you?) may have introduced a styling approach that is browser dependent.

Fonts and their sizing from the previous post is definitely a possible issue. Even if the exact same foundries are available on both systems, the way those render in terms of size, anti-aliasing, and resolution will vary across systems, there is no real workaround for that other than designing your pages with fixed-pixel sizes - which IMO is always a very bad idea. Why bad? Because you lose the ability to resize the text in browser preferences.

---

### Post by pqwoerituytrueiwoq on 2020-06-12
desktop themes will affect stuff like button and input fields defaults on web pages, a web page can override them, but if the page has no css to do so that is what you get

---

### Post by speatzle-2 on 2020-07-28
Ok, Sorry for the long delay. i have figured out that setting the option "[COLOR=#9cdcfe]-webkit-appearance[/COLOR][COLOR=#d4d4d4]: [/COLOR][COLOR=#ce9178]none[/COLOR][COLOR=#d4d4d4];[/COLOR]" in CSS to all elements removes this platform specific default CSS. This Works on Webkit, Chromium/Chrome and Firefox.

---

