# Building a long-term relationship with your Rails applications

## Background

We all know the now-infamous term Omakase.  It is a Japanese phrase meaning "I'll leave it to you.  I trust you."

Omakase is great -- for food.  It lets you try something new.  It lets you trust an expert chef to stretch their creativity and give you something wonderful.  And when the meal is over, unless you get some type of gastrointestinal distress or uncover a previously unknown food allergy, that chef's work is done.  That chef is no longer invested in your happiness beyond wanting you to come back to her restaurant again for another short-term experience.

By now the infamous "Rails is Omakase" phrase should be expired from our drama brains.  No matter how your perception of that phrase is colored -- whether it be "we are the hard-working, knowledgable, benevolent creators and know better than you" or "f__k you, we know better than you" -- hopefully we can all understand the important point.  We don't want the Rails framework to stagnate.  We should be able to trust the smart, hard-working Rails core and contributors to stretch their creativity and give us something wonderful.  Occasionally that leads to some gastrointestinal distress, but often we get the tools we can use to help us build something wonderful too.

If you are a consultant building and handing off greenfield MVP Rails applications to customers, your role is much like that chef trying to wow your customer with what's new.  Those challenges are much different than the challenges of a company that builds and maintains a few core services and needs to keep a product available and updated long-term without interrupting current customers.  And in my news feeds and podcasts, I hear much more about improving those greenfield skills than I do about the long-term maintenance.

I've been developing Web applications since 1999, either working alone or in a tiny team of up to three people.  I've built applications in Perl, PHP and Ruby.  Probably about 200 applications.  The kinds of applications that don't always push the envelope of what is new.  They serve an important purpose, and they do not get retired often.  I have about 40 Rails applications to upgrade every time I get an e-mail from @tenderlove about a new Rails vulnerability.  So keeping all my apps updated and fresh as possible is the best way I can react quickly to urgent upgrades.

But it can be painful to keep a Rails app updated.  Just ask the Github folks how their Rails 3.2.13 upgrade worked out. (https://github.com/blog/1440-today-s-email-incident)  And it's not just Rails, right?  Has everyone gone from Devise 1 to 2 to 3 without a hitch?

Of course we still need to churn out new, fresh apps and features too, so maintenance of these external dependencies can't be our full time job.  

It's important to our overall happiness to ease this pain.  So let's try to help each other out.

## Staying on the Rails on a crazy train

### Rails itself

* http://edgeguides.rubyonrails.org/upgrading_ruby_on_rails.html

The primary source for knowing about big changes from version to version

* railsdiff.org

When upgrading Rails, this is my second stop after edgeguides.  I want to see all the differences in the generated code from one version to another so I can start with a good foundation before I go crawling through my own code for things that need to be updated.

* RailsApps Project - http://railsapps.github.io/updating-rails.html

Daniel Kehoe does a fantastic job keeping this document updated with super helpful upgrade tips

* Ruby and Rails notification groups, podcasts, blogs, the twitters

Sure it seems obvious.  But sometimes you'll get surprised by what you find by digging into the code and diffs in these notifications.  For example, I was pleasantly surprised to learn I could easily patch Ruby 1.8.7 for the floating point overflow CVE from November.  Not that anyone has apps that are still stuck on 1.8.7.

And Twitter?  That's the only place I've heard about the Ruby 2.1.0 BigDecimal bug so far.  

HN and r/ruby are worth a check every once in a while.

### Important gem dependencies

* A simple 'bundle outdated' works

Or you could look at sites like Gemnasium 

* Back to the blogs

Don't ya miss Google Reader?

### Security stuff -- Knowing when to make that upgrade a higher priority

* NIST Vulnerability Database - http://web.nvd.nist.gov/view/vuln/search-results?query=Ruby&search_type=all&cves=on

I love that ruby-doc.org shows that ominous security message at the top.  Ok, love is a strong word.  But it sure is handy and comprehensive, covering Ruby, Rails and Ruby gems.  Unfortunately this site is slow as molasses and often throws errors.

## Design your application to minimize the impact of these fluid external dependencies

* Read POODR. Live POODR. 

@sandimetz wrote this wonderful book -- Practical Object-Oriented Design in Ruby.  When I get frustrated with Rails, I go back to this book to be reminded of why I love Ruby.  When you concentrate on creating objects by first thinking about the messages they will pass to each other, you will minimize the coupling of those objects.

* PORO -- Plain old Ruby objects rock

You can do a lot with a plan Ruby class or module.  And that PORO will likely do the same thing in Rails 4 as it would in Rails 1.

* ActiveRecord stores data.  Is your fat ActiveRecord model doing **so much more** than just storing data?

Composition is your friend.

## Ruby upgrades
* http://blog.mikeleone.com/2013/10/upgrading-legacy-applications-ruby-18.html

## Other references and links to browse for ideas

### Helpful ideas
* http://blog.andywaite.com/2012/12/23/exploring-concerns-for-rails-4/
* http://monkeyandcrow.com/blog/reading_rails_concern/
* http://rubylearning.com/blog/2010/11/02/how-does-one-use-design-patterns-in-ruby/

### Griping
* https://news.ycombinator.com/item?id=7130668

### Other
* http://www.reddit.com/r/ruby/comments/1wa9bs/what_do_you_do_in_the_first_x_minutes_of_creating/
