---
title: "Help with HTML:Parser"
date: 2008-02-26
forum: General Help
---

### Post by pkad on 2008-02-26
Hi,

I just joined this forum, and have a question about the Perl CPAN module "HTML::Parser".

I'm trying to extract the text that is embedded by "certain_tag", which appear several places in a xml file.  

The following code snippet I'm using will stop extracting after the first "certain_tag".  I'm not able to extract the remaining "certain_tag" even though I comment out the $self->handler(end.....) method call.  Thank you for any suggestions.


 use HTML::Parser ();

  sub start_handler
  {
    return if shift ne "certain_tag";
    my $self = shift;
    $self->handler(text => sub { print shift }, "dtext");
    $self->handler(end  => sub { shift->eof if shift eq "certain_tag"; },
                           "tagname,self");
  }

  my $p = HTML::Parser->new(api_version => 3);
  $p->handler( start => \&start_handler, "tagname,self");
  $p->parse_file("file.xml");

---

