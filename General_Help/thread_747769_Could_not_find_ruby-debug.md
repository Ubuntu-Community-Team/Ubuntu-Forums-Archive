---
title: "Could not find ruby-debug"
date: 2008-04-06
forum: General Help
---

### Post by jdonnell on 2008-04-06
I'm using 6.06 LTS and for some reason it can't find certain ruby gems. 

# gem install ruby-debug
Bulk updating Gem source index for: [http://gems.rubyforge.org](http://gems.rubyforge.org)
ERROR:  While executing gem ... (Gem::GemNotFoundException)
    Could not find ruby-debug (> 0) in any repository

I've installed ruby-debug on many different systems and never had this problem. Any ideas?

Btw, I tried clearing the cache and it didn't help
# rm /usr/lib/ruby/gems/1.8/source_cache

---

### Post by jdonnell on 2008-04-07
for some reason it worked the third time I tried it install it :confused:

---

