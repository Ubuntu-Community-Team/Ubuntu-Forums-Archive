---
title: "[SOLVED] Firefox 3.0 cannot display Chinese characters properly"
date: 2008-06-23
forum: General Help
---

### Post by clarezoe on 2008-06-23
I have a really odd problem in my Firefox 3.0

Take this page for example
[http://blog.sina.com.cn/s/blog_494cdb6a010099pp.html]("http://blog.sina.com.cn/s/blog_494cdb6a010099pp.html")

I cannot see the contents of the blog post, but the title and comments are fine.

In the attachment screenshot picture, the left one is in Opera, the right one is in firefox. You can see that there's no content in firefox but you can see the title.

Here's the output from terminal
```

(firefox:8143): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is '&#26999;&#20307;_GB2312 Bold 11.736328125'

(firefox:8143): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is '&#26999;&#20307;_GB2312 Bold 15'

(firefox:8143): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='&#26999;&#20307;_GB2312 Bold 15', text='English Hello'

(firefox:8143): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='&#26999;&#20307;_GB2312 Bold 11.736328125', text=' '

(firefox:8143): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is '&#26999;&#20307;_GB2312 11.736328125'

(firefox:8143): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is '&#26999;&#20307;_GB2312 15'

(firefox:8143): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='&#26999;&#20307;_GB2312 15', text='English Hello'

(firefox:8143): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='&#26999;&#20307;_GB2312 11.736328125', text=' '

(firefox:8143): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is '&#26999;&#20307;_GB2312 9.3896484375'

(firefox:8143): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is '&#26999;&#20307;_GB2312 12'

(firefox:8143): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='&#26999;&#20307;_GB2312 12', text='English Hello'

(firefox:8143): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='&#26999;&#20307;_GB2312 9.3896484375', text=' '

(firefox:8143): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is '&#26999;&#20307;_GB2312 8.2158203125'

(firefox:8143): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is '&#26999;&#20307;_GB2312 10.5'

(firefox:8143): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='&#26999;&#20307;_GB2312 10.5', text='English Hello'

(firefox:8143): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='&#26999;&#20307;_GB2312 8.2158203125', text=' '

(firefox:8143): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is '&#26999;&#20307;_GB2312 Bold 9.3896484375'

(firefox:8143): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is '&#26999;&#20307;_GB2312 Bold 12'

(firefox:8143): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='&#26999;&#20307;_GB2312 Bold 12', text='English Hello'

(firefox:8143): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='&#26999;&#20307;_GB2312 Bold 9.3896484375', text=' '

```

Any help is appreciated!

---

### Post by clarezoe on 2008-06-23
I found the solution.

The fonts folder didn't have the proper permission /usr/share/fonts/zh_CN/ , I gave the user permission to the folder, every thing works!

---

