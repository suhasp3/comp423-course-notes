# Setting up a Dev Container for Go

* Primary author: [Suhas Puttoju](https://github.com/suhasp3)
* Reviewer: [Ishita Siddamreddy](https://github.com/ishitasr76)

## **Prerequisites**
Make sure that you have the following before you start working:

1. A GitHub Account  
2. `git` for version control  
3. Docker downloaded on your device (to run containers)  
4. Visual Studio Code  

## **Part 1: Project Repository Setup**
### Step 1: Creating Local Directory and Initializing Git 
1. Open your terminal/command prompt and create a new directory for your project 
```bash
mkdir go-tutorial
cd go-tutorial
```
2. Initialize a new Git Repository: 
```bash
git init
```
3. We then create a README file
```bash
echo "# Go Programming Language tutorial" > README.md
git add README.md
git commit -m "Initial commit with README"
```

### Step 2: Creating a remote repository on GitHub
1. Log into GitHub and go to the 'Create New Repository' page.
2. Here is what you should fill in for the details of the repo
    * Repository Name: `go-tutorial`
    * Description: "Simple Go tutorial that outputs Hello COMP423!"
    * Visibility: Public
    * Do NOT initialize the repo with a README

### Step 3: Linking the Local Repository to GitHub
1. Add the GitHub repository as a remote 
```bash
git remote add origin https://github.com/<your-username>/go-tutorial.git
```
When doing this, replace `<your-username>` with your GitHub username.

2. Check what your repository's default branch is using `git branch`. The default branch should be `main`.
    * If its not, run the following command to rename it to main: `git branch -M main`.

3. Push your local commits to the GitHub repository
```bash
git push --set-upstream origin main
```
All your changes should be pushed on GitHub now and you should be able to see it 

## **Part 2. Setting Up the Development Environment**
Development Containers are important because it standardizes the envrionment for software development and makes sure your work is replicable across different machines. 

### Step 1. Add Development Container Configuration 
1. Open the `go-tutorial` directory on VS Code. 
    * File->Open Folder->go-tutorial
2. In VSCode, click extensions and install the extension called Dev Containers
3. Create a `.devcontainer` directory at the root of your project and add `devcontainer.json` inside that directory
The configuration should be `.devcontainer/devcontainer.json`
4. In the file you just created, add the following code
```json 
{
  "name": "COMP423 Go Notes",
  "image": "mcr.microsoft.com/devcontainers/go:latest",
  "customizations": {
    "vscode": {
      "settings": {},
      "extensions": ["golang.go"]
    }
  }
}
```
### Step 2: Reopen the Project in a VSCode Dev Container
Type `Ctrl + Shift + P` or `Cmd + Shift + P` on Mac, then type "Dev Containers: Reopen in Container" and select the option


Give it a couple of minutes but once the setup completes, close the current terminal tab. Open a new one and run `go version` to check what version of Go your container is running. 

## **Part 3. Running A Go Program**
### Step 1. Create the Go Project
Now that your Dev Container is set up, lets create a new Go Project


Initialize the Go Module by running: 
```bash
go mod init
```
This will intialize a `go.mod` file in the current directory which defines the module's properties and dependencies

Now we need to write our "Hello COMP423" program. Start by creating a file named `main.go` at the root of your project.
[Here] (https://go.dev/doc/) is the documentation for working with Go but I will provide you with the code for now below:

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello COMP423!")
}
```
Now that our program is written, we can run it!

### Part 2 - Running the main.go file 
To run the Go program, use the `go run` subcommand:
```bash
go run hello.go
```

The output should be 
```bash
Hello COMP423
```

You could also create an executable file by doing `go build`









