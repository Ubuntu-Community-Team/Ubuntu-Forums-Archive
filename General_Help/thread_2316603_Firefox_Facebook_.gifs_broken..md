---
title: "Firefox Facebook .gifs broken."
date: 2016-03-09
forum: General Help
---

### Post by kazakore on 2016-03-09
This has always worked until recently but now on my laptop, updates performed today (Ubuntu Studio 14.04) although I admit I'm travelling and haven't been browsing on my laptop so much so may have been like this for a week or more without me noticing. But suddenly .gifs posted on facebook, for example on media.giphy.com , do not work. You can no longer click on them to get them to animate on the page. You can not click the icon in the lower right to open in an external tab/page. Clicking where it says a link has been posted just takes you to the post (which I would assume is a Facebook bug.)

Works fine on my Android phone and on Apple and Windows PCs of other here with no issues so even if it is due to a Facebook change it is not affect most other users!


EDIT/ADD:
I can highlight with the mouse over where it says media.giphy.com and select View Selection Source from the context menu. This gives me this for one example:
```

<div class="hidden_elem"><div class="_393-"></div><div class="_30b"></div><div class="_30h"></div></div><span><a href="[https://www.facebook.com/l.php?u=https%3A%2F%2Fmedia.giphy.com%2Fmedia%2FVdjkEtKKZunao%2Fgiphy.gif&amp;h=lAQHNEnCx&amp;s=1]("http://ubuntuforums.org/view-source:https://www.facebook.com/l.php?u=https%3A%2F%2Fmedia.giphy.com%2Fmedia%2FVdjkEtKKZunao%2Fgiphy.gif&h=lAQHNEnCx&s=1")" target="_blank" rel="nofollow" onmouseover="LinkshimAsyncLink.swap(this, &quot;https:\/\/media.giphy.com\/media\/VdjkEtKKZunao\/giphy.gif&quot;);" onclick="LinkshimAsyncLink.referrer_log(this, &quot;https:\/\/media.giphy.com\/media\/VdjkEtKKZunao\/giphy.gif&quot;, &quot;\/si\/ajax\/l\/render_linkshim_log\/?u=https\u00253A\u00252F\u00252Fmedia.giphy.com\u00252Fmedia\u00252FVdjkEtKKZunao\u00252Fgiphy.gif&amp;h=lAQHNEnCx&amp;render_verification=0&amp;enc&amp;d&quot;);"><div class="_5b-_"><div class="_6lz _6mb _6o8 ellipsis">media.giphy.com</div><i class="_5aqi img sp_jt1t2Q99FLi_1_5x sx_30552b"></i></div></a></span></div></div></div></div></div></div><div><form rel="async" class="commentable_item" method="post" data-ft="{&quot;tn&quot;:&quot;]&quot;}" action="[/ajax/ufi/modify.php]("http://ubuntuforums.org/view-source:https://www.facebook.com/ajax/ufi/modify.php")" id="u_jsonp_4_p" onsubmit="return window.Event &amp;&amp; Event.__inlineSubmit &amp;&amp; Event.__inlineSubmit(this,event)"><input name="charset_test" value="&#8364;,´,&#8364;,´,&#27700;,&#1044;,&#1028;" type="hidden"><input name="fb_dtsg" value="AQFLcS4liN8Z:AQHfI4ejLUX0" autocomplete="off" type="hidden"><input autocomplete="off" name="ft_ent_identifier" value="10153244648447084" type="hidden"><input autocomplete="off" name="data_only_response" value="1" type="hidden"><div class="_sa_ _5vsi _ca7"><div class="_37uu"><div data-reactroot=""><div class="_3399 _a7s"><div class="_524d"><div class="_42nr"><span><div class="_khz"><a tabindex="-1" role="button" href="[#]("http://ubuntuforums.org/view-source:https://www.facebook.com/#")" data-testid="fb-ufi-likelink" class="UFILikeLink _4x9- _4x9_ _48-k UFILikeLinkHasProgress" aria-pressed="false">
```

Taking the link section alone and converting ASCII:
https:\/\/media.giphy.com\/media\/VdjkEtKKZunao\/giphy.gif

As you can see it has both a forward slash and a back slash each time when it should just be a backslash:
[https://media.giphy.com/media/VdjkEtKKZunao/giphy.gif](https://media.giphy.com/media/VdjkEtKKZunao/giphy.gif)

---

### Post by kazakore on 2016-03-10
Must have been a Facebook error. Working again today with nothing changed this end. Restarted my computer before making the original post but it hasn't been restarted inbetween so definitely no changes this end. Marked as Solved.

---

### Post by nilocesar on 2017-01-18
Well, in my Ubuntu 16.10 installation the GIFs were broken too, and this fixed the issue in my computer:

1) sudo apt-get install x264
2) visit [https://www.youtube.com/html5?gl=BR&hl=pt](https://www.youtube.com/html5?gl=BR&hl=pt) to see if h.264 was installed ok

---

