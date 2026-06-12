---
title: "Ruby on Rails Code Issue"
date: 2007-07-04
forum: General Help
---

### Post by Das Oracle on 2007-07-04
I don't know of a software/programming section to put this in, so general seems the next best thing. I followed a tutorial on creating a classifieds site w/ RoR, however I get the following error:

[my site error]("http://vesoautomotive.dyndns.org:3000")

and here is the code associated with the error:

```
class Classified < ActiveRecord::Base
	belongs_to :category
	validates_presence_of :title,
		:message => "cannot be blank. Make your title descriptive"
	validates_presence_of :price
	validates_numericality_of :price,
		:message => "must be a numeric value (no $ signs or decimals)"
	validates_presence_of :location
	validates_presence_of :description
	validates_presence_of :email
	
	protected
		def validate
			   errors.add(:price, "should be a positive value") if price.nil?
				|| price <= 0
		end
	validates_format_of :email, 
	 :with => /^([^@\s]+)@((?:[-a-z0-9]+\.)+[a-z]{2,})$/i	
end
```

specifically the error is in this line but I do not know how to get proper syntax: 			   errors.add(:price, "should be a positive value") if price.nil? || price <= 0

---

### Post by Das Oracle on 2007-07-04
does anyone know how to change that statement in ruby so the syntax is correct?

---

