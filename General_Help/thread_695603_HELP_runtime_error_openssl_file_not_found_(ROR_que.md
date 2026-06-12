---
title: "**** HELP*** runtime error openssl file not found (ROR question)"
date: 2008-02-13
forum: General Help
---

### Post by Parind on 2008-02-13
I'm trying to run a Ruby on Rails (ROR) application for the first time and can not get Mongrel or WEbrick going. It gives me this error.

from /usr/local/lib/rubygems/1.8/gems/rails-2.0.2/lib/initializer.rb:159 in require frame work : No such file to load: OpenSSL (RunTimeError) and then bunch of lines that looks like this
from /usr/local/lib/rubygems/1.8/gems/rails-2.0.2/lib/initializer.rb:88 in  'process'
from /usr/local/lib/rubygems/1.8/gems/rails-2.0.2/lib/initializer.rb:88 in 'send'
from /usr/local/lib/rubygems/1.8/gems/rails-2.0.2/lib/initializer.rb:88 in  'run'  etc etc etc

So I looked up some forums and installed 'openssl' and everytime I do # apt-get install openssl it tells me that " libssl-dev is already the newest version " so no update is done.
I checked my synaptic software manager and found that libopenssl-ruby, libopenssl-ruby1.8, libssl0.9.8 and libssl-dev packages are installed. 

One other forum said that he went into the ruby-1.8.5/ext/openssl directory and created the
openssl make file by doing make. But I dont have a ruby1.8.5. So I went into /usr/lib/ruby/1.8 and I dont see /ext folder ??????  More over I can not find extconf.rb

One more data that might be useful in diagnosis is that when I go into a Ruby on Rails application and run script/about, it gives me same error. I also did irb and then executed require 'openssl' it says no such file load.

One more data point. I went to [http://wiki.rubyonrails.org/rails/pages/RailsOnUbuntu](http://wiki.rubyonrails.org/rails/pages/RailsOnUbuntu) and reinstalled rails and did $ export PATH=$PATH:/var/lib/gems/1.8/bin like it asks me to but guess what.... I dont have /var/lib/gems/1.8/bin. I rather have /var/lib/gems/1.8 and then no bin. I get a gem folder again. My path there looks like /var/lib/gems/1.8/gems/sources-0.0.1/lib (I dont know but does this mean that I have two different installations ?)

Questions are
1) Does Ghastly Gabon come with ruby installation
2) I dont have /ext/openssl directory, It seems thats the key. How do I create this directory ?
3) How do I remove this runtime error about not finding openssl.
4) Does this path "  /usr/local/lib/rubygems/1.8/gems/rails-2.0.2/lib/initializer.rb "  mentioned above look funny ?

I would appreciate if you can answer any of my questions. I'm really frustrated since I have wasted my whole day trying to solve this.

I have ubuntu Ghastly Giban (Dule core AMD x86)on a dell system with ruby 1.8.6 installed.

---

