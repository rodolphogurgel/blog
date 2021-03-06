## Causal Impact

*KYLE*: So Linh Da, we're going to get into this thing.  It's a paper.  It's a line of research.  It's something that came out of Google and they have a nice R package that implements it.  It's called casual impact.  And I want to talk to you about this in the context of Saturday Night Live.  So right after this we're going to go watch an episode.  So there's all the guests and musical guests.

*LINH DA*: So Kyle is showing me on his tablet, two column lists.

*KYLE*: How many of those people do you know?  I think I knew about half.

*LINH DA*: Do you want me to count them?

*KYLE*: Yeah, just ballpark it.  I knew about half.

*LINH DA*: Half.

*KYLE*: Now let's talk specifically about the musical guest.  Would you say all of these are famous people or what?  What do you think?

*LINH DA*: The musical guests?

*KYLE*: Are they rising stars?  Declining stars?

*LINH DA*: Most of them are famous.

*KYLE*: Anybody you never heard of?  Then we wouldn't know maybe they're famous.

*LINH DA*: Yeah, there seems to be 5-10 I don't know about.

*KYLE*: Do you think these people have growing careers or shrinking careers?

*LINH DA*: Probably growing.

*KYLE*: Even Springsteen?

*LINH DA*: Oh well that one I didn't know about so I can't comment.

*KYLE*: If they're already famous, they're already popular.  People are looking around for them online.  What do you think the impact of being on Saturday Night Live is on their career?  Is it a boost for them?  Do they gain new fans?  What do you think happens?

*LINH DA*: If they're already famous?

*KYLE*: Yeah.

*LINH DA*: Hmm.  Maybe they just get more views and get more influence.

*KYLE*: Do you think they pick up new fans though?  Saturday Night Live is a big deal.  Maybe it's not as culturally relevant as it use to be but there's bands I learned about, because they appeared on that show, that I like.

*LINH DA*: Yeah, I guess I wonder who's whatching SNL.

*KYLE*: Yeah, I don't really watch it anymore.  But I did when I was younger.

LINHDA: What is their segment?  What do the people look like?  Is it older people?  Is it younger people?

*KYLE*: Yeah, but I mean like, it's a big show is my point.  So appearing on it is really good for your career.  But we might like to say: well how good is it for your career?  And does it make you just like famous for a little bit right after?  A little boost?  Or is it sustaining in it's impact on your career?  How would you do that absent of a method like causal impact?

*LINH DA*: I don't know I thought you were going to tell me.

*KYLE*: Well yeah, I was just wondering if you had any guesses.  Like how could we do an A/B test?

*LINH DA*: Well, you could ask people: hey, do you know of Canye West?  What do you think of Canye West?  Do you like him?  Do you not like him?  Do you listen to his music?  And then after he appears on SNL, ask the same question.

*KYLE*: So Linh Da's idea of doing an A/B test here is an interesting one.  If we wanted to take a direct measurement of the impact that an artist recieves from appearing on Saturday Night Live, we could take a random sample of people to call.  We call each of them and ask how popular they think an artist like Kanye West is.  That's a measurement.

Call them back a few days after the broadcast and ask the same question.  Also ask if they happened to watch Saturday Night Live.  Those that did are the test group, those that did not are the control group.  Simple right?

Not exactly.

I've got four quick problems with that approach.  First off, I don't know how you'd get a truly independent and identically distributed sample of people who will answer their phone for a poll.  Doing this will incur a ton of bias and I'm not sure we can account for it.

Out of people that answer the phone, how many will participate in your survey?  How many will answer honestly?  Will anybody ask "Do I get free tickets if I give a high score?"?

Then the idea of calling them back, hmm.  Could the first call have influenced the person?  What if I called you up and said "Excuse me sir, what are your thoughts on the musician [Dan Potthast](http://www.thestitchup.com/)?"  How many of you are going to go [Google that later](https://www.google.com/search?q=dan+potthast)?  It's like the social scientist's quasi-heisenberg uncertainty principle where just by taking a measurement you might alter the state of the system.

So you need a new random sample, because you don't want to talk to people that only watched SNL as a result of the call.  What if the demographics of your before and after groups differ enough to bias the result?  After all a true random sample will have a certain amount of variation.  Perhaps we should then stratify the sample, ensuring we have equal parts men, women, young, old, tall, short, left-handed, right-handed.  Of course the left handed people are rare.  And the two that live in my household are sensationally busy.  You might need to be more aggressive at getting a chance to talk to lefties, but then how identically distributed is that?

But hold on, this sounds like I'm talking about polling.  I said we weren't going to get into election polling until 2017.  Let's move on.

Even if we could address these methodological issues to our satisfaction, there's still good reasons we'd want to use Causal Impact instead.  Causal Impact can account for trends and seasonality in our data.  For example, maybe emerging artists are on a good trajectory and getting more popular independently of the SNL appearance.  We need to detrend the data, and Causal Impact will take care of it for us.  In terms of seasonality, maybe every mid-April in the US, we see a sudden jump in emo and heartbroken country music as people come to grips with paying their taxes.  That one might be a stretch, but Causal Impact can account for seasonality as well.  And there are a few other benefits we'll get into later.

Let's make sure we've got the fundamentals down.  What are we actually trying to measure anyway?  I keep saying popularity, but can we pin that down a little better?

I wanted to come up with a novel use case and I worked with Karen Blakemore to come up with something.  We had to come up with a hypothesis.

*KAREN*: It was that a musical artist that appeared on Saturday Night Live would see an increase in their Wikipedia page views after their appearance.

*KYLE*: What I'd like to measure is the popularity of an artist to see if the SNL appearance causes any boost to it.  Unfortunately there's no unit in SI for popularity.  We'll have to measure it by proxy.  We could, in theory, have looked at something like new Twitter followers.  However, we decided on Wikipedia pageviews.  Taking the time to Google someone or look them up directly on Wiki seems to be a slightly more robust signal than an action which takes only one click.  It's also less likely to be bias in the way Twitter followers might be as the appearance will likely generate a lot of tweets and retweets, thus arguably changing the underlying data generation process that is followed for people to gain new followers.

The causal impact literature generally uses the term "intervention" to describe the event of interest.  This term fits a bit better in a medical context, but I think we may see the definition of intervention slowly drift over time as methodologies like causal impact adopt it to describe a particular event which may plausibly have changed a time series.

We'll obviously be talking about the project results later on, but for the moment, let's consider what we expect the before and after periods to look like.  If we selected a different intervention, such as being featured in your town's local high school newspaper, we presumably wouldn't even be able to notice the intervention at a glance when comparing the before and after period.  Surely SNL has a bit bigger audience, though.

I expect that following the intervention, the amount of people reading about the artist on Wikipedia will immediately spike and then decay.  The decay accounts for people who look up the artist sometime later, which seems less likely to be remembered as more time passes.  Of course people like me don't watch much live television, so their search query will likely occur some random time later whenever they get around to watching, and the longer we wait, the fewer future viewers we're likely to have.  Thus, my expectation is an abrupt spike with some decay, the steepness of which remains to be seen.

Now causal impact requires us to select several other similar Wikipedia pages whose time series of pageviews is likely uneffected by the SNL appearance.  It would be easy to get concensus that the Wikipedia page for statistician [John Tukey](https://en.wikipedia.org/wiki/John_Tukey) should not be impacted by Adele's performance.  But what pages would be good counterfactuals?

What we ultimately decided to do was use an existing music recommendation engine.

*KAREN*: The closer that the other artist was to the artist under consideration the more that it resembled that artist's music.

*KYLE*: So this is a piece of our work which would be reasonable to criticize.  Why should we assume that similar artists would have similar Wikipedia pageviews?  I don't know that I can build a deeply convincing case, but here's my rationale.  Similar artists should have similar audience size.  After all, if we can conclude that 90% of people that like Weezer will also like Ozma, then it's just a matter of time before those audiences will blend when the word gets out.  I expect that as different genres of music experience surges in popularity, the rising tide would have some effect on all artists.  That might not happen evenly, but when such effects do exist, it means similar artists pageviews, which are dependent upon interest in the genre, do therefore contain information about other artists in the same genre.

If we assume the recommendations were 100% perfect, then this would be a perfect measurement.  Now recommender systems are far from perfect, so our similarity choice is bounded by the accuracy of the recommender system.  I could actually build pretty long winded diatribes describing why this is a great approach and why it's not.  One reason I do like this approach is that I don't believe Goodhart's Law would be at play here.  Marketing companies are constantly trying to manipulate the metrics used to measure them.  Some people create bot nets to generate non-human ad clicks.  As far as I know, there don't exist many incentives for people to arbitrarily boost the pageviews on Wikipedia.  In the end, we had to start somewhere, and this is what we choose to be our proxy for popularity.  The skeptical thing to do is to file that away and consider whatever our results are in the context of how strong or weak you find this methodological choice to be.

*LINH DA*: Sure

*KYLE*: And we could even say the same thing about stocks.  Facebook stock and twitter stock and Google's... these are all internet/technology companies and some people, in fact, even invest in like technology funds because they say hey I want to invest in the internet.  I think there's good things happening there.  So, all those stocks, they move up and down together.  One predicts the other.  Does that make sense?

*LINH DA*: Yes.

*KYLE*: So, let's say there was a scandal like one of the CEOs did something terribly scandalous and it was going to hurt the company.  You would want to know what is the impact of this scandalous event?  You could in part predict it by looking at the stocks that correlate.  You could be like, well these stocks all stays the same, but the company with the scandal dropped by 1%.  And they tend to move together, so you could use that information to help predict the impact, wouldn't you say?

*LINH DA*: Mmm hmm, yep, yep.

*KYLE*: No there's also the regular trend.  If you just looked over the past time, let's say of one of these artists, and you said how popular have they been the last couple weeks or months, and you said, well I expect this trend to continue, then you know into the future, ok, my prediction was it would continue in this manner, whether that's increasing or decreasing.  So you also have information from the time series before the intervention.  And lastly, you might have some knowledge that you can represent in a bayesian way.  That's something that actually we should talk about more on this show, I don't think I mention priors enough, but this would be an idea like, well, you could say that maybe you knew in general appearing on any TV show, whether it's Saturday Night Live or not has some known range of how much benefit it generally gives a person between 0 new fans and a billion new fans.  Actually, you know it's not going to be a billion new fans, that's unreasonable.  So, I could take that information and represent that in a bayesian way.  So I have three sources of information that can help me predict the future.  I have the time series, the data before appearing on the show, how popular someone was.  Then I have, I could compare them to maybe similar artists.  What do you think of that idea?

*LINH DA*: Yeah, good thinking.

*KYLE*: Yeah, so like, if it's Kanye, is he technically a rapper?  What sort of performer is he exactly?

*LINH DA*: I guess rapper.  Pop.  Hip-hop, pop, rap, rapper.  He likes to do everything.  He likes to think of himself as an ar-teest.

*KYLE*: I've heard he thinks quite a bit of himself actually.

*LINH DA*: Yes, yes.

*KYLE*: We could find other people in a similar class as him and say maybe there's a cultural place for that and look at how he compares to other similar artists.  And then lastly, we can maybe encode some prior information if we had any about general changes.  So what causal impact can help us do is look at all those factors and then make a forecast into the future of given those three sources of information, how do you think the popularity of a person would have continued into the future.  And then if you compare that to the observed popularity, you can back into what the difference was and then you can look at the actual impact of that intervention and how it changes over time.  So for example, do you think appearing on Saturday Night Live would make you more popular in the next week?

*LINH DA*: I guess.

*KYLE*: Almost certainly.  The question is whether it's a little or a lot, but it's gonna happen.

*LINH DA*: Yeah.

*KYLE*: What about five years later.  Do you think people are still talking about who was on Saturday Night Live?

*LINH DA*: No.

*KYLE*: The impact levels off over time, probably.  The cumulative impact.  So this can help us learn things about how interventions effect stuff.  So we're going to talk about it in the context of Saturday Day Night Live, but it can also work in stocks and a lot of media and like advertising campaigns and things like that use causal impact.

*KAREN*: I think the idea is very useful to try to tease out the impact of different intervetions on a time series.  I think it could be used in a lot of different applications including different marketing campaigns.  Maybe looking at software defects and software reliability at different releases with different interventions that you might want to do.

*KYLE*: So Causal Impact has obvious applications in marketing.  You want to know if a TV campaign is effective on your brand, you can show it in one region and not others.  Although regions are unique, the degree to which they historically have been predictive of each other can be exploited.  Use the data from the regions that didn't see the TV commercial to forecast what would have happened in the market that did.  The different between actual and predicted is the assumed impact.

When Karen and I were working on Causal Impact I asked if she could find any novel examples of it's use that weren't in marketing, since there's lots of talks and examples that apply in marketing.  Karen found this really interesting paper titled "Causal Impact for App Store Analysis" by William Martin at University College London.

*KAREN*: Right, yes.  He was looking at the impact of releases of mobile apps and the measurement that he was using was the reviews of the releases or ratings of the releases.

*KYLE*: Welcome to the show, William Martin.

*WILLIAM*: I've been, throughout my PhD, doing app store analysis where I mine large collections of apps from appstores like Google Play, Windows Phone Store, and Blackberry.  I perform empirical analysis on them to look at what are the trends and relationships between attributes like rating, download rank, and price.  We also mine features from descriptions and look at any associates that those have with performance metrics like rating and download rank as well.  This is also, sort of, at the snapshot level.  This is all what we see at any given point in time.  But I've always been more interested in how things change and evolve.

*KYLE*: If I had started a project like this, I might come into it saying, well, it seems like causal impact would be very useful.  Let's just see what we get out of this.  Was this sort of exploratory or did you have some really direct goals in mind.

*WILLIAM*: This was very exploratory when we started.  Firstly, we had this time series dataset and we wanted to check whether what we've heard about frequent releasing strategies... are frequent release strategies a good thing?  And so we looked at the absolute correlation between number of releases in a time period and performance.  And we were kind of surprised to find that simply releasing doesn't increase performance.  But then causal impact analysis allows us to look at individual releases and see what makes an individual release impactful or not impactful.  Or, what makes it have a positive effect or a negative effect if it's impactful.  Then our goal became, what are the common themes among these impactful releases.  What are developers doing that could increase their performance?

*KYLE*: William was regularly crawling iTunes and capturing data about ratings, reviews, and releases.  If, hypothetically, a beloved app that gets all 5 star reviews unexpectedly switches their free services to a paid premium service and locks users out from the app without subscribing, it stands to reason a sharp rise in 1 star reviews would appear, and William could correlate that to the release.  That's an extreme case that might not require causal impact to understand, but most cases are a lot more subtle than this.

Speaking of 5 star reviews, now might be a good time for you to head over to iTunes, if you use that, and give Data Skeptic a review.  This helps other people find the show.  If enough of you start rating, maybe I could do something similar to what William did to evaluate the impact individual shows have on the popularity of Data Skeptic.

*WILLIAM*: I cam across this technique called Causal Impact analysis that takes as input a time series metric such as the rating that an app has every day for a year.  We can use this technique to see if an intervention has a significant effect on that performance metric.  If an app were to have a release that was so good that everybody said, hey, I'm going to rate 5 stars now, and cause the app's average rating to increase significantly, then the tool would pick this up.  So I use this technique called causal impact analysis to identify all of the releases in my data sample that had a significant impact on rating or download rank or the rate at which users were reviewing the app in a year time period.  And then I looked for common factors among those releases.

Many app developers try to push updates quite rapidly because the code bases of apps are very small and rapid release strategies have been gaining traction.  And so developers do try and release frequently but the updates tend to not contain very much content.  And so, many of these releases, for instance releases that simply contain bug fixes, were detected as not being very significant.  We perform the analysis on all the analysis that didn't have an impact and found that bug fixes were quite a large component out of those releases.  At least in the most popular apps.  We actually conducted a subsequent study on the apps that appear in the most popular apps at some point in the last three years but don't remain there.  So these are the sort of apps that are bubbling under the surface, trying to become more popular.  For those apps, bug fixes are actually a good thing.  But literature in the field has found that a lot of updates to do with apps are just to update advertising libraries.

*KYLE*: I struggle a little bit with that interpretation.  If bug fixes don't have a positive impact, is it that those bugs were just minor and not important, and people were annoyed by the download?  Or what's your interpretation?

*WILLIAM*: I should clarify again.  This results about the bug fixes was actually different between the most popular apps and the ones that are just sort of bubbling underneath and perhaps trying to be more popular.  It does seem that fixing bugs should be a positive thing.  But for some reason isn't in the very popular apps in the app store that remain in the most popular free and paid lists.  But, it doesn't seem to be such a bad thing in the contender apps.

*KYLE*: So perhaps bug fixes that are correcting a significant defect are impactful but fixing a typo or corner case isn't as relevant.  It seems like it might be a bit hard to pin down.

*WILLIAM*: It's not easy to say if it's a good thing or a bad thing.  It may be the case that an app has to keep updating frequently just to maintain the status quo.  But it's kind of hard to test that in a scientific experiment.  What we did find was that there was no absolute correlation between the number of releases and an app's current performance, such as it's rating or it's reviewing frequency.  There was no correlation there.  So it's not the case that simply pushing out releases is going to increase your performance, but it's difficult to say more than that.

*KYLE*: Sure, yeah.

*WILLIAM*: But what we found was simply releasing more frequently doesn't increase your chance to be popular.  We looked more at the content of releases and found that releases that talk about new features and talk about bigger overhauls of the app and the code were more likely to make the release be impactful and to have a positive impact.  But simply releasing just for the sake of it didn't seem to increase performance.

*KYLE*: Do you see any seasonal variation in the average ratings people are giving in the app store.

*WILLIAM*: There isn't much seasonality component that we observed.  It seems to be pretty consistent over the year time period.  Although when we've spoken to developers, they have said that they recieve a big boom around Christmas time.  We looked at the deviation over about a year and found that ratings tend to be quite stable, and this is reflected in the impacts we observed.  The impacts in rating tend to reflect pretty small changes in the overall rating, but this is likely because the apps we're looking at have recieved tens to hundreds of thousands of reviews at this point, and so, it would require thousands of people to rate significantly differently than the mean in order for that to change.

*KYLE*: I see. So you only have access to the cumulative ratings.  Is that right?

*WILLIAM*: Yeah. The cumulative.  We have the number of five, four, three, two, and one star reviews.  We have that information.  The rating frequency does deviate pretty significantly over a year time period.

*KYLE*: So you had mentioned looking at the review text which seems like a really powerful data source.  But it starts as just raw text.  Can you tell me a bit about the feature extraction work you had to do to get something useful out of it.

*WILLIAM*: We take the "what's new" text from Google apps.  Google has this text component for developers to explain what's changed in the app.  We first filter that for stop words, punctuation, perform lemmatization, which is something that makes words that are saying the same thing such as fast and faster, share the same word, but it's a slightly more readable result than stemming.  And then we perform topic model on this.  Topic modeling is a technique that you can use to extract the main themes of text from a set of documents.  So in our case, the document is the "what's new" text in each of these releases.  And then we looked at the top most prevalent themes in each of these groups.  And when I say group, I mean impactful releases or non-impactful releases.  Or impactful releases that increase the rating, or impactful releases that decrease the rating.  And then we looked at the top topics in these.  This is where we found that some of the most prevalent things that are being talked about are bugs and features but the other terms that came out of this analysis were really quite specific to individual apps and categories.  So it was hard to go further with that technique.  So what we did after that was we looked at simply how prevelant are mentions of bug fixes in each of these release groups.  This is where we found that bug fixing isn't such a good thing for the most popular apps but new features does seem to be much more prevalent, well it is much more prevalent in impactful releases and in ones that increase the rating.


*KYLE*: So in causal impact, one has to have a counterfactual to compare against.

*WILLIAM*: Yeah.

*KYLE*: What are you using in your analysis.

*WILLIAM*: For my analysis, the counterfactual is the set of non-releasing apps.  The apps that we recorded that don't have any releases over the year time period.  And we did find that the performance metrics for this counterfactual control set was very very stable over the year time period for these apps.

*KYLE*: I believe there are some worthwhile takeaways in your paper for app developers.  Could someone use your methods to predict if their upcoming release will be impactful?

*WILLIAM*: So our work is really retrospective.  We can only really answer questions about this dataset that was mined between 2015 and 2016 and say here's what happened to impactful releases and here's what happened to non-impactful releases.  Unfortunately, we can't really predict what's going to happen.  We can't really predict what developers should do to their apps.  But I think it would be very very interesting if someone was able to do that.  There's only so much you can do with past data unfortunately.

*KYLE*: That makes sense.  William's use of causal impact explores the impact of a particular release based on how it was rated before and after, compared against non-releasing apps.  This is similar to our Saturday Night Live project.  Trusting that the number of page views an artist's page on Wikipedia gets is a reasonable proxy for popularity, we want to measure how impactful the appearance was on their overall popularity.  Before we get into the results, Linh Da and I wanted to immerse ourselves in this topic, so we decided to watch one episode from last season.

*LINH DA*: Hmm, I don't know.  I like Sia.

*KYLE*:  What is Sia's style?  What kind of ska does she do?

*LINH DA*: She's ballads.  Pop Ballads.

*KYLE*: Pop ballads.  Ok.  We could watch that.

*LINH DA*: Maybe Miley Cyrus.

*KYLE*: Ok.

*LINH DA*: I don't know.  Which one do you want to watch?

*KYLE*: I'm pretty open.  Actually, let me take a look.  Gwen Stefani...

*LINH DA*: Mmm k, we can watch Gwen.

*KYLE*: No, we can watch Miley Cyrus, either one.  Miley Cyrus is the opening so that might have been a strong one.  Oh, Tina Fey and Amy Pohler, that could be good.

*LINH DA*: Who's the musical guest?

*KYLE*: Springstein.

*LINH DA*: I don't really like Springstein.

*KYLE*: What about this Courtney Barnett?  Do you know who that is?

*LINH DA*: Is that an actress or a performance?

*KYLE*: That's a musical performer.

*LINH DA*: We could do that.  Just someone we don't know.

*KYLE*: Well let's go watch Fred Armison and more importantly Courtney Barnett.  Especially she's a good example because I've never heard of her.

*LINH DA*: Yeah, so we're going to comment on what we think.

*KYLE*: So that means either I'm out of touch or she's an immerging artist, which will make it more interesting to look at this analysis.  And after we're done, we're going to look at a page on dataskeptic.com that the listeners can also check out to do the causal impact analysis on exactly this data.

*LINH DA*: So Kyle's really excited about this.

*KYLE*: Yes, it's a very cool project.

(Fair use clip of "Nobody Really Cares if you Don't Go to the Party" by Courtney Barnett)

*KYLE*: We'll check in again with Linh Da in a bit.  For now let's get back together with Karen to discuss how we can actually implement a causal impact analysis.

*KAREN*: Google developed a R package to measure causal impact given a time series of interest and a control time series, as well as the intervention period.  Wikipedia supplies an API to retrieve pageviews on a daily basis for any article.

*KYLE*: So all the pieces are there for us to do our analysis.  We can pull the pageviews for any article on Wikipedia thanks to an API they provide.  Causal impact is implemented in an R library.  We can look up the guests, and their dates of appearance and plug them in.

*KAREN*: And then use the R Shiny App to develop a web application where a user could input a wikipedia article they were interested in, control articles, and the time period under consideration, and when the measurements should be started and ended.  It displays graphs showing the time series before the event occurred, during the event, and then after, as well as the time series that would have resulted had the intervention not taken place.  The difference between those two after the intervention determines the impact that your intervention had on the time series.

*KYLE*: Great, so now we have a tool to do our exploration.  We put this up live if you want to try it out yourself.  It's available at snl.dataskeptic.com.  We'll also be uploading a video that walks through the usage of the app if you're interested in learning more.  You can also fork the project or just check out the code on github if you're curious.

There's one interesting gotcha to using the results which Karen noticed as we were exploring the data.

*KAREN*: Right.  It has to be adjusted for the standard time that's used by Wikipedia.  Wikipedia uses UTC time which is 4 hours later.  So Saturday Night Live appears at 10:30pm eastern time.  So the spike that you'll see in pageviews occurs on the day after the Saturday Night Live appearance.

*FRED*: We've got a great show for you tonight.  Courtney Barnett is here.  So stick around.  We'll be right back.

*KYLE*: Alright Linh Da.  So post monologue check in.

*LINH DA*: I don't like Fred Armisen.  He's boring.

*KAREN*: So, what I found was that the impact was short-lived.  That a musician's pageviews increased for only about one day after their appearance.  Then they seemed to go right back down to the level of pageviews prior to appearing on Saturday Night Live.

*** *KYLE*: Of course, every artist's intervention should be looked at separately.  I haven't had a chance to do this yet, but I'd like to go back and see what happened to Ashley Simpson as a result of what happened to her on an appearance quite a few years back.  But for the artists I did check using the Shiny app that Karen built, her description is apt.

Within the assumption that pageviews on Wikipedia are a good proxy for a person's current popularity or cultural relevance, an appearance on Saturday Night Live does not appear to have a sustaining impact on popularity but does result in a noteworthy immediate spike.

*WILLIAM*: At UCL, we've launched a spinout company called Apppredict.  We preform analysis services for developers like this.  We can perform causal impact on their apps and we can also analyze their compeditors, optimize keywords, and things like that.

*KYLE*: For the average developer, how much impact do you think that has?

*WILLIAM*: It could potentially be very useful.  We use techniques in our research that other appstore optimization companies just aren't using, don't have.  Because in research, we're generally on the bleeding edge of what's possible.  And so I think it could be quite beneficial for developers if they were to take advantage of this.

*KYLE*: You had mentioned that AppPredict is spinning out of UCL.  That's University College London?

*WILLIAM*: That's right.  Causal Impact analysis at UCL was really only myself.  I started using this for appstore analysis.  But several in the systems and software engineering group got very interested in causal analysis and so we actually hosted a workshop on causal impact analysis earlier this week and had the author [Kay Brodersen](https://people.inf.ethz.ch/bkay/) give a very interesting talk.

*KYLE*: A link to [Apppredict Limited](http://crestweb.cs.ucl.ac.uk/appredict/) is in the show notes as well as William's papers.  Let's check back in with Linh Da whose finishing watching an episode of SNL and then get a final thought from Karen on causal impact.

(Fair use clip of "Pedestrial at best" by Courtney Barnett)

*KYLE*: So Linh Da, now that you've had your exposure, the first two songs you've listened to by Courtney Barnett, what do you think of her?

*LINH DA*: N'ehh.  I don't really think much...

*KYLE*: Not your style?

*LINH DA*: I'm going to forget her and the band.

*KYLE*: Could you maybe describe the style?  What is her music like to you?

*LINH DA*: I thought it was pop inspired by the 80s.  Her style of singing is monotone, nonchalant, without emotion.  Partially inspired by English singers like The Smiths, I assume.

*KYLE*: You don't get like a Joan Jett vibe from her?

*LINH DA*: I don't know Joan Jett.

*KYLE*: Ok.

*LINH DA*: Why does everyone keep saying that?  Don't you hate that when someone references something and you're like, uh huh, and then later they bring it up and you're like "I don't know that, stop bringing it up".

*KYLE*: Well haven't you had time to check the reference?  I mean, isn't that how things go?

*LINH DA*: And plus like, if you don't know Joan Jett, why would I reach out and learn about them?

*KYLE*: I don't know.  Cultural milestone?

*LINH DA*: The odds are I'm not going to like Joan Jett if I don't like this person.

*KYLE*: Well I'm going to keep making Ghostbusters references if that's what this is about.

*LINH DA*: People just make me look up stuff I don't like.  I'm like, I know I'm not going look up more stuff.

*KYLE*: Alright, so you're not a fan of her yet but do you think she picked up a lot of new fans?  How many new fans do you think she picked up?

*LINH DA*: Well there's probably millions of viewers of SNL so all you need is 1% of people to like you.

*KYLE*: At this point I'm pulling up [snl.dataskeptic.com](http://snl.dataskeptic.com) to show to Linh Da.  You can pull it up to if you want to follow along.

*KYLE*: The dotted line, that's the prediction of how many pageviews she would have gotten and the blue area is the confidence interval.  Then the black line is the actuals.  So that's what her real downloads were.  So clearly it wasn't predicting a big spike, and she did get one.  But then what happens to that spike?

*LINH DA*: It drops off.

*KYLE*: Yeah.  Does it drop off to the old levels or does it have a bit of a lift.

*LINH DA*: No it's higher.

*KYLE*: Yeah, she got a little lift!  So it appears if we judge her popularity by her Wikipedia pageviews, it definitely benefited her to be on the show.  She got more popular.

*LINH DA*: Yup.

*KYLE*:  We don't see that when I check other artists.  Kayne West, for example, and Sia, both died off very quickly.  But it looks like Courtney here, she got a little bit of a lift.  It might have even doubled her pageviews, it's hard to say with the scale there.

*LINH DA*: Yeah I don't know, I can't tell.  Her original views are so low.

*KYLE*:  Does it surprise you she might have acrewed a bunch of new fans?

*LINH DA*: That's what I expected.

*KYLE*: Final thoughts on Causal Impact.

*KAREN*: I think there's a lot of different applications for it.  It's very easy to use being written in R.  So yeah, I think it's a great concept and useful tool.


Check out our app by visiting [snl.dataskeptic.com](http://snl.dataskeptic.com).
