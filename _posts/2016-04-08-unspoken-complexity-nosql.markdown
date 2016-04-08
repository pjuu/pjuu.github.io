---
layout: post
title:  "Un-spoken complexity of NoSQL"
comments: true
disqusid: 29f52fa5-508b-4ab7-8a69-5f5c629b403c 
date:   2016-04-08 19:15:00 +0000
categories: pjuu nosql mongo choices 
---
The first blog post I am going to write about is how choosing NoSQL on small projects brings a lot of extra baggage.

```
TLDR; Please think before using NoSQL. There may be great success stories and you may have had a bad SQL experience. That isn't SQL's fault though.
```

When I started to write Pjuu I was working as a sys admin at a managed hosting company along with Ant (the other Pjuu admin).

Working in this environment you get the impression SQL isn't the way to go. A lot of people run their companies on it and it causes them no end of problems. I have a lot of experience with MySQL/MariaDB and I can confirm that there are a huge number of people which just wing it. The decisions you have taken choosing a datastore are based on things they never thought of. They cut their teeth on MySQL so everything they ever did invloved it. Yet these are the same people that don't understand the differences between MyISAM and InnoDB. Patterns of accessing your data are put on the back burner because they know MySQL and that's that.

As a young, impressionable Linux admin I always thought; "These are big companies making millions of pounds a year! There databases are soooo bad that maybe SQL isn't up to the job". I think this is becoming a general way of thinking. Personally afters 100's of bad experiences with SQL, I blamed SQL and not the users/developers of it.

Enough of the back story. When I wrote Pjuu initially I chose to use Redis and only Redis because of the bad experiences I've had. Sounds daft, no? It should do because as a sole database it did not work. There was a lot of code to deal with simple problems where SQL would have excelled.

The next move I made was to change parts of Redis out for MongoDB. This helped a lot in the earlier stages of development.

I like MongoDB. I have been using it for a few years now, have completed the Mongo university qualifications and all was going great, I sang it's praises.

After leaving another managed hosting company I took the plunge and became a developer. Coming from a sys admin background my Python knowledge had grown to the point I realized I would never get use it if I didn't make the move. I went to work for a company which used MySQL and struggled with the exact same issues I had working in hosting. Only this time I had to make it sort of work as I was the one working with it. With all the MySQL experience I thought I had, running very large systems using it I couldn't get past the poor choices previosly made in the database design (this was the worst case I'd ever seen). This just made the NoSQL/MongoDB route appeal all the more.

With this job I was travelling a long distance to get to work. I did enjoy it because I got to work with Python everyday and it was great. The job was in Django then and I could hide the mess behind the ORM. We got what needed to work, working.

I then left the company due to illness and moved closer to home. To another company that used MySQL (I am now using Coldfusion, which is terrible, I'll get to the point...). When I say MySQL it is MariaDB and the company is what would be classed as an enterprise although it is a small company. It is owned by a very big UK company.

I decided Coldfusion was shite (and it truely is. Sorry to swear). The only thing I had a semi-interest in was SQL. So all the work I was tasked with I pushed as much as I could in that direction.

That is when I had an epiphany (not the Jesus kind, I'm athiest). SQL was working for us!... How could a company using Coldfusion have a decent SQL story? It seemed impossible. The database design isn't great, it doesn't follow any nice clean patterns but it works. It is the first place I had been where the MD (primary developer) of the company actually knew what he was talking about when it came to SQL.

At that same time I was having doubts about the NoSQL movement. I realized the Pjuu source code had some complexities. Lots of list comprehensions to decide what we need to get from MongoDB next. It just started to seem silly.

I also fell in love with types and MongoDB/Python didn't seem to fit.

To catch up with the present day. Pjuu is stil written in Python, uses Flask as the web framework and still relies on MongoDB and Redis.

I have been following PostgreSQL for 6-7 months now and I'm falling in love with it more and more. Listening to the community around it had gotten me over MySQL PTSD (sorry for  using that term lightly. I lost friends durning my stint in the Army). I can see SQL/RDBMS again as the amazing tools they are. So much so that once the last few main features we want in Pjuu are implemented I am whole heartly going to pull MongoDB out and re-write Pjuu.

I think for for an open-source social network using a technology that had a lot of power is the best way to go. It is very hard to get people interested in contributing to a project. Never mind one with complex code due to database choice.

I know I've not said any techical thing here. That isn't the point of this post. The point of this post is that I thought NoSQL was the future. I had a lot of experience in sys admin land and development land and still came to that conclusion. It is only as I keep coding away on a NoSQL project that I more and more realize I was wrong. NoSQL may work once you become the next Twitter but not as you flesh out your project(s).

P.S. I'll hopefully write posts about maintaining test suites. Pjuu has 100% coverage test suite which is very hard to cope with. That may have lead to some of my NoSQL annoyances. 
