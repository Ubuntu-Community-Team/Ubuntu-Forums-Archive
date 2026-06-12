---
title: "Ruby on Rails app root"
date: 2012-10-16
forum: General Help
---

### Post by pmatos on 2012-10-16
Hello,

I am trying to set up redmine on 12.04. 

I did run :
```
apt-get install redmine redmine-mysql
```

It installed a whole bunch of deps. I can't get passenger to work. When I try to access redmine, I get:
```

The directory "/var/www" does not appear to be a valid Ruby on Rails application root. 
```

On > /etc/apache2/mods-enabled/passenger.conf I have:
[HTML]<IfModule mod_passenger.c>
  PassengerDefaultUser www-data
  PassengerRoot /usr/lib/phusion_passenger
  PassengerRuby /usr/bin/ruby
</IfModule>[/HTML]

And in my virtual domain apache config I have:
[HTML]       <Directory /var/www/paulomatos.com/subdomains/projects/>
              RailsBaseURI /
              PassengerResolveSymlinksInDocumentRoot on
        </Directory>[/HTML]

I can't understand where passenger grabs that /var/www from. How shall I proceed?

---

