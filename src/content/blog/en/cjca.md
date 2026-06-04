---
title: "CJCA: Preparation, Tips, and Common Mistakes"
description: "I share how I prepared for the CJCA, what I learned during the process, which mistakes you should avoid, and some recommendations to take the exam with more confidence."
pubDate: 2026-06-03
heroImage: '../../../assets/cjca.jpg'
lang: "en"
---

In this post, I want to share a guide based on my experience preparing for and passing the Hack The Box CJCA certification.

Throughout the post, I will talk about my preparation, the importance of practicing with a methodology, the weight that documentation carries, the analysis part in Elastic/Kibana, and some mistakes that are worth avoiding before and during the exam.

---

## My General Opinion About the Certification

In my opinion, CJCA is a very good starting point for those who want to begin developing a more complete view of cybersecurity, because it combines two worlds that are often studied separately: Red Team and Blue Team.

On one hand, it forces you to think like an attacker: enumerate services, exploit vulnerabilities, gain access, escalate privileges, and move through an environment. On the other hand, it also requires you to analyze evidence, review logs, validate alerts, interpret suspicious activity, and justify why something does or does not represent a real threat.

Something important you need to understand is that the assessment is not designed as a series of completely isolated challenges. It is not only about solving one point, finding a flag, and automatically moving on to the next one. The approach is closer to a practical scenario, where it is useful to analyze the context, organize the available information, and make decisions based on what you observe.

That is why an important part of the process is learning how to ask good questions:

* What information do I have available?
* What information am I missing?
* Is what I found actually useful?
* Does this file contribute anything to the objective?
* Does this event provide additional context?
* Can this evidence help me better understand another part of the environment?
* What information should I keep and what can I discard?

That mindset shift is key. A finding by itself does not always mean much. What matters is asking whether it actually adds value, whether it can be validated, whether it is related to another point in the environment, or whether it helps build a better understanding of the scenario.

The same applies to files, logs, users, processes, network connections, or any other data found during the assessment. Not everything will have the same level of importance. Part of the difficulty lies in interpreting the available information, identifying what is relevant, filtering out noise, and understanding how the findings connect to one another.

For that reason, I believe this certification evaluates much more than technical knowledge or the use of tools. It also tests your working methodology, analytical ability, and the way you document your findings.

---

## How to Prepare for the Certification

One of the most common questions before taking CJCA is whether the Hack The Box preparation path is enough to pass the certification.

Hack The Box requires completing its preparation path, and in my opinion, it is a very good foundation. The content starts with fundamental concepts and gradually moves toward more practical topics such as networking, Linux, Windows, enumeration, exploitation, WordPress, tool usage, and evidence analysis.

Although the path includes practical exercises, I believe we should not rely only on that. The content gives you the foundation, but for the exam you also need to develop your own working methodology.

**What do I mean by methodology?**

I mean the series of steps we follow when approaching an environment, from initial enumeration to exploitation, post-exploitation, evidence analysis, and documentation. In each phase, we need to have a process: knowing what to review, how to interpret the information, how to validate a hypothesis, and how to decide what the next step should be.

For example, it is not just about running tools, but about understanding what we are looking for. During enumeration, we need to identify services, versions, technologies, and possible attack paths. During exploitation, we need to validate whether a vulnerability actually applies to the environment. During post-exploitation, we need to analyze what information we found, what permissions we have, what access we can expand, and how all of that relates to the final objective.

That is why I believe the best way to prepare is to complement the path with Easy Hack The Box machines, both Linux and Windows, or with similar labs. By practicing in different scenarios, we face different services, errors, technologies, and exploitation paths, which helps us build a stronger methodology.

At first, this methodology may feel like a rigid checklist: scanning ports, enumerating services, searching for vulnerabilities, testing credentials, reviewing permissions, documenting findings, and so on. But as we solve more machines, the process becomes more natural and organic.

In the end, preparing for CJCA is not about memorizing commands or answers, but about learning how to investigate, correlate information, and build an organized way to solve problems.

---

## Recommended Machines for Practice

Something important I want to clarify is that I do not recommend these machines because they are the same as the exam or because they necessarily contain the same attack vectors. I recommend them because they help develop a working methodology, which for me was one of the most important skills during preparation.

The idea is not to memorize exploitation paths, but to practice the full process: enumerate, interpret the information, research technologies, validate hypotheses, exploit when appropriate, review the compromised system, and document the findings.

| Linux | Windows |
|---|---|
| Lame | Return |
| Broker | Legacy |
| Cap | Blue |
| Keeper | Devel |
| Blocky | Optimum |
| Backdoor | Bastion |

Even so, I do not think you should limit yourself only to these machines. Ideally, you should keep practicing until you feel that your methodology is solid enough across different scenarios.

My recommendation is to try solving them on your own first. This helps you identify your own weaknesses: what things you did not enumerate, which services you overlooked, which commands you forgot to run, or where in the process you got stuck.

After trying, you can complement your work with videos, writeups, or guides to compare your path with other people’s approaches. The idea is not to copy the solution, but to detect missing pieces in your methodology and incorporate them into your own way of working.

The Easy machine catalog on Hack The Box, both Linux and Windows, is quite broad. However, I think it is important not to move too far away from the scope of the preparation path.

For example, if the path does not go deep into Active Directory, then spending time practicing AD environments should not be a specific priority for CJCA. It can be useful for your general growth, but it is not necessarily the most important thing when preparing for this certification.

Use these machines as a starting point, but not as a definitive list. The real goal is to build a methodology that you can apply in different scenarios, not to memorize a specific exploitation path.

---

## What About the Blue Team Part?

In my case, I have to be honest: outside of the content included in the preparation path, I did not do too much additional practice focused specifically on Blue Team.

However, if you feel this is your weakest area, or if you simply want to arrive with more confidence, **Hack The Box Sherlocks** or similar labs can help you a lot. These types of challenges focus on evidence analysis, incident investigation, event correlation, and building conclusions from logs.

This is important because in the Blue Team section, it is not enough to see an alert and mark it as **True Positive** or **False Positive**. You also need to explain why you reached that conclusion.

For example, imagine an alert related to multiple failed login attempts. A very basic way to justify it would be:

> Five failed login attempts were observed, followed by a successful login for the same user.

The problem with that explanation is that, by itself, it does not say much. It could be a user who forgot their password, a typo, or a legitimate attempt. The key is to investigate what happened before and after that successful login.

A more complete explanation would be:

> Five failed login attempts were observed against a privileged account from the same IP address. Minutes later, a successful login was recorded from that same IP. After the access, reconnaissance command execution, file downloads to a temporary directory, and execution of a privilege escalation-related tool such as JuicyPotato were identified. This sequence allows us to conclude that it was not only a set of isolated failed attempts, but a possible intrusion followed by post-exploitation activity.

The difference between both examples is important. In the first one, we are only mentioning isolated events. In the second one, we are building a timeline: failed attempts, successful access, command execution, tool download, and possible privilege escalation.

That type of analysis is much more useful for a report, because it does not only explain what happened, but also why those events are related to one another and how they support the conclusion.

That is why, when practicing Blue Team, my recommendation is not to stop at the initial alert. Try to answer questions such as:

* Which user was involved?
* From which IP did the activity occur?
* Was the login successful after several failures?
* What processes were executed afterward?
* Were any files downloaded?
* Were suspicious directories such as `/tmp`, `Temp`, or `Public` used?
* Does the activity match reconnaissance, persistence, privilege escalation, or lateral movement?

In short, for the Blue Team section, you do not need to memorize every possible alert. What matters is learning how to investigate, build a logical line of analysis, and justify your conclusions with clear evidence.

---

## Mistakes You Should Avoid

After going through the preparation process and taking the exam, there are several mistakes that I think are important to mention. Some of them I made directly, while others I identified during preparation or while building the report.

The purpose of this section is not to scare you, but to help you avoid problems that can affect your performance, especially when time is limited and you need to maintain an organized workflow.

### Mistake 1: Not Reading the Instructions Carefully

When you start the exam, you will receive important instructions about the scope, objectives, and the way you should approach the assessment.

One of my main mistakes was not reading them carefully enough. I assumed I already knew where to start and began investigating a path that was not the priority at that moment.

It may seem like a minor detail, but in a practical certification, time is a very valuable resource. Spending several hours on the wrong investigation path can affect the rest of the exam.

My recommendation is simple: before running a single command, read the instructions completely, identify what they are asking for, and clearly define what your first objective should be.

### Mistake 2: Not Documenting From Minute One

One of the best decisions I made was documenting everything from the very beginning.

In my case, I used Obsidian as my main organization tool. The idea was to build my report while taking the exam, so that later I would already have a large part of the work done when completing the final template in SysReptor.

Every time I obtained a relevant result, I immediately added:

* The command executed.
* The result obtained.
* The corresponding evidence or screenshot.
* Important observations.
* Possible next steps.

This allowed me to keep a clear history of every action performed and avoid having to reconstruct processes hours later.

I also recommend reviewing **Bruno Rocha Moura’s** resource about CPTS reports:

> [Read the CPTS report resource](https://www.brunorochamoura.com/posts/cpts-report/)

Although it is focused on CPTS, many of the documentation, structure, and evidence presentation principles also apply to CJCA. It can serve as an excellent reference to understand how to present findings in a clear, organized, and professional way.

### Mistake 3: Relying Too Much on Memory

After several hours of exam time, multiple hosts, commands, credentials, events, and findings, it is very easy to forget important details.

What seems obvious when you find it can be difficult to remember when writing the report. That is why I do not recommend depending on memory.

To avoid this, I organized my notes in Obsidian by creating one folder for each machine or exam section. There, I saved the relevant information as I found it.

For example:

* Users.
* Passwords.
* IP addresses.
* Flags.
* Important files.
* Interesting locations.
* Credentials.
* Relevant commands.
* Quick notes about possible investigation paths.

This allowed me to centralize the important information and have it available when I needed it, without depending on remembering every detail at the end.

### Mistake 4: Not Giving the Report the Importance It Deserves

If there is one thing I would like to emphasize about this certification, it is the importance of the report.

It is easy to fall into the idea that finding the flags is the most important thing, but the report is the real evidence of all the work performed during the exam.

Think of the report as the way you are going to demonstrate your findings. It is not enough to reach the final result; you also need to explain how you got there.

During the exam, I tried to ask myself these questions:

> How would I explain this step to someone else?

> What would an evaluator need to see in order to understand how I got here?

A flag by itself means very little if there is no logical line explaining the process. What truly adds value is demonstrating how you investigated, what decisions you made, what evidence you found, and why you reached a specific conclusion.

If you find relevant information, gain access to a system, or identify suspicious activity, you must be able to explain what you did, what you observed, and how that evidence supports your finding.

That is why I recommend thinking about the report from the first minute of the exam, and not only when it is time to write it. The better documented your process is, the easier it will be to build a clear and solid narrative.

### Mistake 5: Not Taking Enough Screenshots

One of the recommendations I received in the exam feedback was to take more screenshots.

During the exam, I felt that I had enough evidence, but when writing the report, I realized that in some parts the narrative felt incomplete. I knew how I had reached certain findings, but I was missing screenshots to better demonstrate the process.

Because of that, I had to go back and collect additional evidence from points that I had not documented as well as I thought.

My recommendation is simple: document every relevant step. If you are unsure whether a screenshot is worth taking, it probably is.

It is better to have more evidence than you need than to discover at the end that you are missing an important screenshot to explain how you reached a finding.

## Conclusion

Overall, I consider CJCA to be a very interesting certification for those who want to develop practical skills and have a first experience with scenarios closer to a real environment.

What I liked the most about the certification is that it is not limited only to exploiting machines or finding flags. It also requires analyzing information, connecting evidence, justifying conclusions, and documenting findings clearly.

If I had to summarize what I learned during this experience, I would highlight several important points:

* Build your own methodology.
* Practice beyond the preparation path.
* Learn how to investigate and ask better questions.
* Document from the first minute.
* Do not underestimate the importance of the report.
* Think like an investigator, not just like someone looking for a flag.

In the end, CJCA does not only evaluate technical knowledge. It also tests the way you approach a problem, how you interpret the available information, how you connect different findings, and how you communicate your results.

My final recommendation is to prepare for the certification calmly, practice with intention, and give documentation a lot of importance. The more organized your process is during preparation and the exam, the easier it will be to build a solid report and truly demonstrate the work you performed.