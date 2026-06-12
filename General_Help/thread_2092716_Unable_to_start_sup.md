---
title: "Unable to start sup"
date: 2012-12-08
forum: General Help
---

### Post by michaeljmcd on 2012-12-08
Whenever I attempt to start Sup, I get the following error:

/usr/local/lib/site_ruby/1.9.1/rubygems/custom_require.rb:36:in `require': superclass mismatch for class Iconv (TypeError)
        from /usr/local/lib/site_ruby/1.9.1/rubygems/custom_require.rb:36:in `require'
        from /usr/lib/ruby/gems/1.9.1/gems/sup-0.12.1/lib/sup/rfc2047.rb:19:in `<top (required)>'
        from /usr/local/lib/site_ruby/1.9.1/rubygems/custom_require.rb:36:in `require'
        from /usr/local/lib/site_ruby/1.9.1/rubygems/custom_require.rb:36:in `require'
        from /usr/lib/ruby/gems/1.9.1/gems/sup-0.12.1/lib/sup/source.rb:1:in `<top (required)>'
        from /usr/local/lib/site_ruby/1.9.1/rubygems/custom_require.rb:36:in `require'
        from /usr/local/lib/site_ruby/1.9.1/rubygems/custom_require.rb:36:in `require'
        from /usr/lib/ruby/gems/1.9.1/gems/sup-0.12.1/lib/sup.rb:351:in `<top (required)>'
        from /usr/local/lib/site_ruby/1.9.1/rubygems/custom_require.rb:55:in `require'
        from /usr/local/lib/site_ruby/1.9.1/rubygems/custom_require.rb:55:in `require'
        from /usr/lib/ruby/gems/1.9.1/gems/sup-0.12.1/bin/sup:15:in `<top (required)>'
        from /usr/bin/sup:19:in `load'
        from /usr/bin/sup:19:in `<main>'

This occurs for both sup installed via rubygems and sup installed via the sup-mail package. Does anyone know how to clear this issue?

---

