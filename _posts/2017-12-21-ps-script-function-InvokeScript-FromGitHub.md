---
layout: post
title:  "Function: InvokeScript-FromGitHub"
date:   2018-11-21
desc: "PowerShell Function to pull script from github and execute it on system"
keywords: "Jekyll,gh-pages,website,blog,powershell,scripting"
categories: [Powershell]
tags: [Powershell,Jekyll]
icon: icon-html
---

```Powershell
Function InvokeScript-FromGitHub ($github_script_raw_uri){
    $github_script_raw_uri = "https://gist.githubusercontent.com/hclpandv/76739cc615f3eee0d4722243379d3/raw/9573fa17aadee9f0b5fb71d38cccefde8b4a220b/CheckSumCalc.ps1"
    $temp_script_file = "$pwd\temp.ps1"

    Invoke-RestMethod -Uri $github_script_raw_uri -Method GET | Out-File $temp_script_file
    & $temp_script_file
    Remove-Item $temp_script_file -Force
}
```


