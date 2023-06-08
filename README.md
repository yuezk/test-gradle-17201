Repo to reproduce https://github.com/gradle/gradle/issues/17201

## Reproduce steps

1. Clone the repo
2. Run `./gradlew copyDependencies` and it works well
3. Modify `app/build.gradle`, change the `copyDependencies` task as follows:
    ```
    task copyDependencies(type: Copy) {
      from configurations.runtimeClasspath.files // <--- here is the change
      into "$buildDir/dependencies"
    }
    ```
4. It will throw an error when running the Gradle tasks.

> It works well with Gradle 7 and Gradle 8, but fails on Gradle 6.9.3
