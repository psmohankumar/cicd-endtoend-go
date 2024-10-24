FROM golang:1.22.5 as builder

WORKDIR /app

COPY  go.mod .

RUN go mod doenload

COPY . .

RUN go build - o main .

#EXPOSE 8080

#CMD ["./main"]

# The aboive two commands are commented  in order to use distroless images

# Final stage - Distroless image

FROM gcr.io/distroless/base

COPY --from=base /app/main .

COPY --from=base /app/static ./static

EXPOSE 8080
CMD ["./main"]