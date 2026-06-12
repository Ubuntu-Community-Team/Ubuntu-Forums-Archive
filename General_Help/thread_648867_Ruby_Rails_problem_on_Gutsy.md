---
title: "Ruby Rails problem on Gutsy"
date: 2007-12-24
forum: General Help
---

### Post by tefflox on 2007-12-24
Please help me troubleshoot the following.  I'm trying to install rails 2.0 over rubygems 1.0.1 ---

```
jess@linux:~$ sudo gem --version
1.0.1
jess@linux:~$ rails test
The program 'rails' is currently not installed.  You can install it by typing:
sudo apt-get install rails
bash: rails: command not found
jess@linux:~$ sudo gem install rails
/usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require': no such file to load -- zlib (LoadError)
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/package.rb:10
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/format.rb:9
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/installer.rb:11
         ... 11 levels...
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/command_manager.rb:103:in `process_args'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/command_manager.rb:74:in `run'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/gem_runner.rb:39:in `run'
        from /usr/local/bin/gem:22

```

---

