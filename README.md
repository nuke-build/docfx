# <a href="https://nuke.build"><img src="https://github.com/nuke-build/all/raw/master/images/icon-glossy.png" width="20" /></a> Nuke.DocFX

<!-- BEGIN DESCRIPTION -->

This NUKE addon provides a [CLI wrapper](http://www.nuke.build/getting-started.html#clt-wrappers) for [DocFX](https://dotnet.github.io/docfx):

<blockquote>DocFX is an API documentation generator for .NET, and currently it supports C# and VB. It generates API reference documentation from triple-slash comments in your source code. It also allows you to use Markdown files to create additional topics such as tutorials and how-tos, and to customize the generated reference documentation. DocFX builds a static HTML website from your source code and Markdown files, which can be easily hosted on any web servers (for example, <em>github.io</em>). Also, DocFX provides you the flexibility to customize the layout and style of your website through templates. If you are interested in creating your own website with your own styles, you can follow <a href="http://dotnet.github.io/docfx/tutorial/howto_create_custom_template.html">how to create custom template</a> to create custom templates.</blockquote>

<!-- END DESCRIPTION -->

## Example

```csharp
using System;
using Nuke.Common;
using Nuke.DocFX;
using static Nuke.DocFX.DocFXTasks;

class Build : NukeBuild
{
    public static int Main() => Execute<Build>(x => x.Example);

    Target Example => _ => _
        .Executes(() =>
        {
            // docfx build docfx.json --output=output --template=template1,template2
            DocFXBuild(s => s
                .SetOutputFolder("output")
                .SetTemplates("template1", "template2")
                .SetConfigFile("docfx.json"));

            // docfx metadata project1 project2 --output=output
            DocFXMetadata(s => s
                .SetProjects("project1", "project2")
                .SetOutputFolder("output"));
        });  
}

```
## Contributing

[![Contributors](https://img.shields.io/github/contributors/nuke-build/docfx.svg?style=flat-square&label=contributors&logo=data%3Aimage%2Fpng%3Bbase64%2CiVBORw0KGgoAAAANSUhEUgAAAFgAAABACAYAAACeELDCAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAAHYcAAB2HAY%2Fl8WUAAAAZdEVYdFNvZnR3YXJlAHBhaW50Lm5ldCA0LjAuMTnU1rJkAAAEFUlEQVR4Xu2bjY3UMBCFrwRKoAQ6gA6gA64D6AA6gA6gA%2BgAOoAOjg6gg2XeSl7lfN%2FGdjweR9E%2B6ZNO7%2BIZjzc%2Fjr17dzqdtvLc%2BGD8MJL0tzz9j9rsmSH1oFnBO6MkHUNt98iwetAs8MWolY6lGHtiaD1ortDSmaTPBsXaA8PrQfMKb4ytUluKOZOQetC8woOxVWpLMWcSUg%2BawL3RK8Wg2DMIqwdN4JfRK8Wg2DMIqwfNjBeGlxSLcqzx1vhm5PNTefoftVkjtB40M94bXlIsykFogv%2FXKEnH6FiKQYTWg2bGV8NLikU5luis2HIJq03NFRJaD5oZPw0vKRblSHhcvqVBjqynaoBrLtNaKRblEBoYj1yKsTbIUfWcQTPDW5RDiynehV9boPEW5biAZoa3KIdmBN5STMrlLcpxAc0Mb%2BXxe15ZS6JXWm%2Fl8R%2BBZsboh0LPK2tJ9Eq7u4fcyGnNK2O0lGOZc3fTtI%2BGl%2FKJ%2BXdjtJRjmXNkPU9AM8NjbpqUP9mjtMw5sp4noAn8MXr121jGjLg9JOW3iRH1IGgCI5b3PC%2FVkpRrmXt3y5Wi51NX2zye59O8JHrae9eDoHkF7y2W2QPsXQ%2BC5gra8GvVtU1Cz1fjkq5t8XjWg6BZoGUeuTZPjBb1QXjVg6BZQc2idWmOGC3qQ8KjHgTNSjQHpJmAvOL80IjUP4P6sKS3HgTNjGfGS0PbMp8M7YeJtV0H3fPScWq3x4ecplnqW%2Brn2pqIak3HaQzUTmOiscnjPgJN47Whb714LcRQgbMH2Cu%2FxkhjpTHLczwaYH0a%2BmRGPN1p5Z8ux1FSrjz%2FqDo1hpczOyXTJTx62pRfTj3z0Fbltyj1ZaQ0luecSubx2lij6CKXmvXh3iuZ1322JJqgz1iuFC1z3x49KFmU9EHmhUZcPbQoE3VSnZNFKl82FB5Lh9dEizKRy6TnhJGiV82RZzGdvVG3h7OUMFr0VjRiTkxzX%2BUOlZJGi85iPeX1OuslxcpnDiL07JWUdIboq03yPAZZMSh%2B6L03Ke%2FEbDQ%2F7RlktaUH6TTQnIzOPm0otkpt6MydCpo7QPdPrR%2FUnM06RsfSPXc6aO4IDVpJuxzYBJqBaNqkdVX9TFWrUFr2S%2BuuomYBSscs2yiGYimmYk%2B9baA5iDSQGoAtPxHolXIqdxp46qM7aDqhs1PF6Hu6o5dCt0h9Ut%2FUx81bQiXQ7EQr%2ByO%2BUD1a6jPuSvSA5kY0%2F5xx6XtLNbjNpdHcgO5tR5NqolqbQLORyL21aNFeXhNoNhK2eD1BtEnQBJqNHF1UczVoNnJ0Uc3VoNnI0UU1V4NmI0cX1VwNmo0cXVRzNWg2cnRRzdWg2cjRRTVXg2YjRxfVXA2aN%2FxA84YfaN7wA80bXpzu%2FgPmTK3HK79ikgAAAABJRU5ErkJggg%3D%3D)](https://github.com/nuke-build/docfx/graphs/contributors)
[![Jenkins Build](https://img.shields.io/jenkins/s/https/jenkins.nuke.build/job/addons/job/docfx/job/release.svg?style=flat-square&label=jenkins&logo=%20data%3Aimage%2Fpng%3Bbase64%2CiVBORw0KGgoAAAANSUhEUgAAACgAAAAoCAYAAACM%2FrhtAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAAAZdEVYdFNvZnR3YXJlAHBhaW50Lm5ldCA0LjAuMjHxIGmVAAAGBklEQVRYR82YfayWcxjHT%2B%2BnkuQlU2e9iE6MiJS%2FakOLFCvOJHGY1kRYRqNh2LAOUXZaTJFWMubloGYtm7Nl8tZ0hlUzJ0dFRVGhF53j8%2F093%2Ftxnufc9%2FNyTjbf7bvf77qu73Xd93M%2Fv%2Fv3cpe0BU1NTaWNjY0Xw2nwSbgMroK1cD38BK5BtxTeT380bSen%2FzfgAj250G1wLTyIHQtih%2BE%2BeMSuAOxf4bOwzCWPDajdjaKPwX2pS2UC%2Fx9wGd0K2v607Z3XHrsvvAJWwXrr%2F4T3Rbo2gSKnU%2BwbFc4G%2FqNwETzF8pwgRTc8Gf7g%2FDdhF4eLB8m9o2LZwL8fjre0KJCuobLKdd6gaedQcSB5pYpkA%2F9fcJRlrQJlOlFjtevNsrtwkNQfHlWBbOCfYVmbQKkTqPUjPAD72J0fiLvCFanbyYSLtRg3%2BE6DI5AMgR3sjgU61R8I9QJNcd35DucH4reVlATiYy3VUzgf%2B%2BNUJI0BDseC%2BPSULNTa43YvTaklyUCoCTUfKqSlHYL%2Bd3gEvgofgnNDoRxAUw4Xkb%2BU9rtQEdCfYEkyED1tfSyIC%2F2trUmZjRNDcitAyQ7kL3Tt%2FH8zonckTgLxWkulHQ%2FvsJkGPq02NchzTh9oytF8RHsD1OqzzqFkIArzUxKIT7U0EWietzY9FdHXSvIh7vTqgX0mPAS%2FhZvhboeSgWi5iseBmMZaD0sTgWak9cvtkq%2FavvPsCsCeZ%2F%2FfUCtT7pUF7SNKiAPJDZYlAllHtWg%2Fhwdh2BjQjnWNBbYrYR2slT8Cdm%2FFE4Gg%2BUvym9sAYodoeloaCzTacmm79bVzZspPV%2Buw%2Fkrd9NlwDvwF6qlp87DD%2BoGhUBwI3mTROpoL7XtYvgjYVwdxDAhrj7gGhq0Y7VY42GHVuhTqhrbAvvIh6wz1JmvaUc6gIM4GsY4Ed8Bt9I%2BTkLYdbZkSI2Df45REINM6exJti%2B0Ufm2zVKcepm%2BG%2Fkv2xy95BC6wYB7sAXWzsx3TAN4G70SSf7bPA%2BrMgoL2hyfb95Yc2N2CKBvEokGs5Bvdv9uxGZhtvrHmoOYcX6PKtsatNsTxcyfB6Ak%2BB%2B%2BFm%2BBQh1sNagyHGX8btjYJL%2Fh6mjM1lHQc2GhJSyDSuNkJd8ET7W4zqKXDlFaJ66H%2BHb3lh31zX0HtgsI4p13htHgg0BiTUHPYGfJh9qOvbX1YfwsF%2BuPdzlTNCNh6i7X7uZm2qzT0KxwLQyoRaPSo51usF%2BMz2GD7WsvyAu25cA%2FU8lYGr4R3wUnwVF9Hvu%2FhdXCxr1HYkEI4Dq4lJ0zU9KsdKgjoR8DNztUT2wh1QNL41s1vdUzr8O1wN9QbXdzZhKSwN6R9wq4A7NlQW%2FXYSRW%2FnpLG9FT4PtSKIWgVGQp%2FhkvQaD95Tdw1CgJ5nUncCzPeLuzJLvq4XWngewbqqU1DEtZl2nawFPZSPwiB%2Buj0BUKbkOQlLhdIjKaDc%2BySrwtsgDqflNsdgD0Y7nKOdtsb6H5Bq4m%2B3rIA7InWpXc9RYN8nTmExXYFYE9IucONXmR3AHYf%2BBTcADW%2B9Bdrv6e%2Fu7s1OjXqpg9wjZxnmJwg%2BTKKROeOYXYHYGuA621XbCEs6JsLukEweom0pOY%2Fi2SDJB1s3lORCNjb4XBLArBHwS2Oa0LWOaUScwDMeCvx66k9CvdL3xz43qXpZ2kyEOkwrYEeZvts4NfTehmOwexFq7kt6aOSvnBpydQ0E%2FZ7uYBG%2F1T8kYK4NpS3wp0peeEgR%2BvoXLgEbrc7AFs7lDQwV8ORUOeROrvTwCeM8W2lgGMYXG9NQUD%2FAc3r7q90Kf1Q7SunwC8Vi4D9E5xkWQD2AoezMd2SIHoAZnxoLATkaK6LlsXXXC4D%2BC%2BBL8Jq2OITHb6qUCwL%2BK8KAvqaiGM%2FEBUDasTeYD6Q94pLZAD%2FWZYE0af2txrUqHG5NHBrTI%2Bj1ecNfRYR9flXf%2F%2Fl%2BKfThu8yzYFP55l%2Fv2XjuCUVaj2osYlGN9QdjoZ6YcKGoFiQV%2BdbSwGfvj%2Fry1KbQA0te8diuLRc9nA%2BCLX3%2Bz%2BwMnVXJSX%2FACrjqI7wt59WAAAAAElFTkSuQmCC)](https://jenkins.nuke.build/blue/organizations/jenkins/addons%2Fdocfx%2Frelease/activity)

If you want to contribute, please first get personal with us about your intentions [on Slack](https://publicslack.com/slacks/nukebuildnet/invites/new). This largely increases the chances for pull-requests getting accepted and helps us establishing a clean and meaningful design of new features. At the same time it reduces the chances of duplicated work.


## License

[![License](https://img.shields.io/github/license/nuke-build/docfx.svg?style=flat-square&logo=data%3Aimage%2Fpng%3Bbase64%2CiVBORw0KGgoAAAANSUhEUgAAAEAAAABACAYAAACqaXHeAAAAAXNSR0IArs4c6QAAAARnQU1BAACxjwv8YQUAAAAJcEhZcwAAHYcAAB2HAY%2Fl8WUAAAAZdEVYdFNvZnR3YXJlAHBhaW50Lm5ldCA0LjAuMTCtCgrAAAADB0lEQVR4XtWagXETMRREUwIlUAIlUAodQAl0AJ1AB9BB6AA6gA6MduKbkX%2BevKecNk525jHO3l%2Fp686xlJC70%2Bl0C942vjV%2Bn9FreVQbBc0wWujfRpW8Z78JaIb53hhJ1ygTA80w9PQ36duBMjHQHPCuoQZfutSjeqU1PAJN4E3j2pN7aVKv6pnWcgGawNfGa5N6prVcgGZBn8yvVXZXQbOgPXokXaPMNZwoc41D%2FaHZ8b7hpBrKjnCizIjD%2FaHZ8aPR6%2BeZXqqh7Agnyow43B%2BaZz40qnQ36a6rlsYgnChDLOkPzTN1z%2B9PafU0N3OAcaIMsaQ%2FNBufG1X9JyrtDMr0Y4xwokxlWX%2BPjAYdemhPrWeDvYcPJ8r0LO3v4oszNfivQQuTp2u9qJGKE2V6lvZ38UVj9q3t3oqEE2U2lvfXF4t6qPjTqDUV1fRyhw8nymws768vfOr2NtqOqFY4UUZE%2BusL6VDRX7%2FGzOHDiTIi0t9WMPsUKzNPx4kysf62gmuHir3sPXw4USbWny485ZOc2PsJ7VTro%2F3pwp5DxV7qHq2xa41TrY%2F2J7PfJkaHir3UwwdtU061PtqfTP0CUaYm2v3LxCtoDI2lMWk8p1of7Y8K0jhRJgaaYZwoE0P%2FpFUndZqtP6T4BE2zC5qtP6T4BE2zC5qtPyRN8OvhZUQae3ZBtT7anyb49PA6Ivp5wKnWR%2FvbJkncZXr6wokysf62CXRCWjmJxhqd2JwoE%2BuvTqS37JGJlB39GLzhRJmN5f31gz8XTpSJgWYYJ8rEQDOME2VioBnGiTIx0AzjRJkYaIZxokwMNMM4USYGmmGcKBMDzTBOlImBZhgnysRAM4wTZWKgGcaJMjHQDONEmRhohnGiTAw0wzhRJgaaYZwoEwPNME6UiYFmGCfKxEAzjBNlYqAZxokyMdAMoL%2FO%2BNi4bzjpT1e%2BNFb8V7gFzUXMLHqk%2BM1A8wArFj1S5GagOUly0SMtuxloTnJrUU%2B7QXOSW4t62g2ak9xa1NNu0Jzk1qKednK6%2Bw9roIB8keT%2F3QAAAABJRU5ErkJggg%3D%3D)](https://github.com/nuke-build/docfx/blob/master/LICENSE)

Copyright &copy; Sebastian Karasek, Matthias Koch.

This project is provided as-is under the MIT license. For more information see the [LICENSE file](https://github.com/nuke-build/docfx/blob/master/LICENSE).

[![Built with Nuke](http://nuke.build/squared)](https://nuke.build)
